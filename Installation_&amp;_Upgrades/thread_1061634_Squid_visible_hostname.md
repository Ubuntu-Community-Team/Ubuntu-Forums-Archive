---
title: "Squid visible_hostname"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by cantdrive55 on 2009-02-06
I am trying to setup squid on my computer at home while I'm at school but I'm getting an error. I have modified my /etc/squid/squid.conf file so that the visible_hostname is the same as my computer, "ubuntu-server" however it still gives an error:

```
jclifford@ubuntu-server:~$ sudo squid -f /etc/squid/squid.conf -z
[sudo] password for jclifford:
2009/02/06 01:08:45| parseConfigFile: line 3049 unrecognized: 'ubuntu-server'
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 2
Aborted

```

---

### Post by Partyboi2 on 2009-02-06
> 2009/02/06 01:08:45| parseConfigFile: line 3049 unrecognized: 'ubuntu-server'Looks like you have a problem with it not recognizing 'ubuntu-server'. Check that you have added the hostname correctly.

---

### Post by cantdrive55 on 2009-02-06
This is my output from /etc/hosts

```

jclifford@ubuntu-server:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       ubuntu-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Partyboi2 on 2009-02-06
Go to line 3049 of your /etc/squid/squid.conf and make sure it looks like this
```
#  TAG: visible_hostname
#    If you want to present a special hostname in error messages, etc,
#    define this.  Otherwise, the return value of gethostname()
#    will be used. If you have multiple caches in a cluster and
#    get errors about IP-forwarding you must set them to have individual
#    names with this setting.
  [COLOR=Red]visible_hostname ubuntu-server[/COLOR]
```

---

### Post by cantdrive55 on 2009-02-06
Duh, I didnt have the "visible_hostname" part. I just had the hostname without the tag. Thanks for helping me out.

---

