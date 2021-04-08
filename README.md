# Note: `firewalld must be enabled` 
# required enable port  `80,443`<- ONLY ... AND allow incoming
# `Not use UFW because DOCKER not work nicely with ufw.` 

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)
## _a tutorial using fail2ban for self-hosted server on linux😊_




## Installation



```sh
sudo apt install fail2ban
```
jail.conf
```sh
sudo gedit /etc/fail2ban/jail.conf
```
jail.conf
```sh
[bitwarden]
enabled  = true
filter   = bitwarden
port    = http,https
logpath = /home/*/bwdata/logs/identity/Identity/log.txt
action = iptables-allports[actname=bitwarden,name=bitwarden,protocol=all]
         iptables-allports[actname=bitwarden-docker,name=bitwarden-docker,protocol=all,chain=DOCKER-USER]
maxretry = 1
```
 `# save`
 
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

bitwarden.conf
```sh
gedit /etc/fail2ban/filter.d/bitwarden.conf
```

bitwarden.conf
```sh
# Fail2Ban filter for Bitwarden
# Detecting failed login attempts
# Logged in bwdata/logs/identity/Identity/log.txt

[Definition]
failregex = ^\s*\[Warning\]\s+Failed login attempt(?:, 2FA invalid)?\. <HOST>$
```
 `rename to [Warning\]` and # save.


## fail2ban-client 



| fail2ban-client | COMMAND |
| ------ | ------ |
| stop | fail2ban-client stop|
| start | fail2ban-client start |
| status | fail2ban-client status |
| status bitwarden | fail2ban-client status bitwarden |
| ban-ip 111.222.333.444 |  fail2ban-client set bitwarden banip 111.222.333.444 |
| unban-ip 111.222.333.444 | fail2ban-client set bitwarden unbanip 111.222.333.444 |

## TEST



First Tab:

```sh
sudo fail2ban-client stop
```

Second Tab:

```sh
sudo fail2ban-client start
```

Third Tab:

```sh
sudo fail2ban-client set bitwarden banip 151.131.111.111
```


Fourth Tab:

```sh
sudo fail2ban-client status bitwarden
```

 `# SHOW`

```sh
Status for the jail: bitwarden
|- Filter
|  |- Currently failed:	0
|  |- Total failed:	0
|  `- File list:	/home/q/bwdata/logs/identity/Identity/log.txt
`- Actions
   |- Currently banned:	1
   |- Total banned:	1
   `- Banned IP list:	151.131.111.111

```

## Fail2ban

bantime  =  VALUE 
 This parameter sets the length of a ban.
 `-1 as a forever` 
`Unit: second `

findtime = VALUE
 This parameter sets the window that fail2ban will pay attention to when looking for repeated failed authentication attempts. 
 `600 = 10 minutes` 
`Unit: second `







**Free Software**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
