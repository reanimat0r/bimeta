# bimeta client

bimeta client is a tool for interacting with bimeta api. It allows authorized users to view and manage metadata and configuration files used by various bimeta intelligence collection plugins.

# Prerequisites

bimeta has been tested on Linux, Windows, and OSX platforms, but should run on any platform supporting Python 3.5 or greater.

# Installation

bimeta can be installed with pip:

```
pip3 install bimeta
```

Verify install:
```
bimeta --help
```

# Configuration

bimeta must be configured with your API keys. You will receive your API keys when you are onboarded to bimeta. bimeta client expects the keys to be placed in a file named bimeta.config.  The client will look for the file in the following order:

* env variable BIMETA_CFG
* ~/.bimeta/bimeta.config
* CWD/bimeta.config

## Examples

You are onboarded and the following API keys are provided to you:

```
defaultAffiliation: someorg
apiKey: d96b1fc40a0ce7b83984eebd6fc1e13f886052cc0721b45e
apiUrl: http://SOME-BIMETA-SERVER:443/bimeta
awsApiKey: 0AATy09KGArpEpqDk3id4vRYPPbJYb3aaQjzIxF2
apiSecret: da9e03275f945596e8752aa6a04fa373559bd22857706b988d6a4c8c8c0eb53ec0b78a910ec28dfc326b707b2c47da2c
```

### env variable example
* Paste the api keys in a file named bimeta.config and put it in /home/myuser/
* Set BIMETA_CFG env variable to point to this file ``` export BIMETA_CFG=/home/myuser/bimeta.config ```
* Start using bimeta ``` bimeta get user ```

### cwd example
* Paste the API keys into a file named bimeta.config and put it in /home/myuser
* Go to /home/myuser ``` cd /home/myuser ```
* Start using bimeta ``` bimeta get user ```

### bimeta config dir example
* Paste the API keys into a file named bimeta.config and put it in ~/.bimeta/
* Start using bimeta ``` bimeta get user ```

# Using bimeta

bimeta client is organized in a familiar VERB - ACTION scheme. For example, command ``` bimeta get user ``` retrieves information about a user from bimeta. Similarly ``` bimeta put user ``` adds a user to bimeta whereas ``` bimeta delete user ``` deletes one.  bimeta client follows the Unix philosophy, so it reads from STDIN, and writes to STDOUT which makes it very friendly for scripting and automation.

## Getting help

bimeta client features rich context sensitive help. Adding --help to any stage of the command is a good way to learn about the capabilities.

### Examples - help
```
se7en@badpanda$ bimeta --help
usage: bimeta <command> [<args>]
    Commands: get|put|set|delete|check|configure

bimeta client

positional arguments:
  command     Subcommand to run

optional arguments:
  -h, --help  show this help message and exit

blueintel -tr
```

```
se7en@badpanda$  bimeta get --help
usage: bimeta get [-h] [--noverify] [--json]
                  {user,ip,tag,config,org,cred,credsource,keyword,authorization,authcred,role,roleperm,userrole}
                  ...

Retrieve data

positional arguments:
  {user,ip,tag,config,org,cred,credsource,keyword,authorization,authcred,role,roleperm,userrole}
                        VERB - type of data to retrieve.
    user                Retrieve user data
    ip                  Retrieve IP data
    tag                 Retrieve tags
    config              Retrieve configuration files
    org                 Retrieve orgs
    cred                Retrieve tracked compromised credentials
    credsource          Retrieve tracked sources of compromised credentials
    keyword             Retrieve keywords
    authorization       Retrieve authorization data
    authcred            Retrieve authentication credentials
    role                Retrieve roles
    roleperm            Retrieve role permissions
    userrole            Retrieve user to role mappings

optional arguments:
  -h, --help            show this help message and exit
  --noverify            Accept unverifiable certificates
  --json                Return results as json
```
