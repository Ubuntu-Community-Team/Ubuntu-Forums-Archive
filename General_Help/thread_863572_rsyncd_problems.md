---
title: "rsyncd problems"
date: 2008-07-18
forum: General Help
---

### Post by jamiesan on 2008-07-18
I am trying to set up rsync on my main server so that I can update things on it, and have my other machines grab the updates.  Everything starts correctly.

my rsyncd.conf file looks like this:

```

motd file = /etc/rsyncd.motd
# for pid file, do not use /var/run/rsync.pid if
# you are going to run rsync out of the init.d script.
pid file = /var/run/rsyncd.pid
#socket options=

# MODULE OPTIONS
[home_jamie_test]
path = /home/jamie/test/
comment = My test
use chroot = yes
uid = nobody
gid = nogroup
include = *
read only = yes
#list = yes
auth users = jamie
secrets file = /etc/rsyncd.secrets
max connections = 10
syslog facility = daemon
lock file = /var/run/rsync.lock
transfer logging = yes
log file = /var/log/rsyncd.log
timeout = 600
```

My command from the other desktop machine looks like this:

sudo rsync jamie@arctos::home_jamie_test

I transferred rsyncd.conf, squid.conf and xorg.conf into my test directory to try to get this to work.

and the output after I type in a password looks like this:

drwxr-xr-x         144 2008/07/18 10:28:17 .
-rw-r--r--        1144 2008/07/18 10:27:47 rsyncd.conf
-rw-------      116111 2008/07/18 10:28:00 squid.conf
-rw-r--r--        1360 2008/07/18 10:28:17 xorg.conf

The problem is that it doesn't actually transfer anything.  My /home/jamie/test directory on the machine I am running the command from is empty.

Can anyone give me a hand with this?  I've done search after search and come up with nothing that seems relevant to my issue.

Thanks in advance.

Jamiesan

---

### Post by jtniehof on 2008-07-18
If you want to copy over everything in the directory, you need to use one of the -r or -a options on the rsync command line. You should also specify a target directory, so your command line would look something like ```
sudo rsync -a jamie@arctos::home_jamie_test .
```

---

### Post by jamiesan on 2008-07-18
Ah!  Thanks!

---

