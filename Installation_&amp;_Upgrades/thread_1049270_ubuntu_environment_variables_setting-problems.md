---
title: "ubuntu environment variables setting-problems"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-01-24
In windows if I want to set an environment variable, I will do it in the control panel/ advance/ environment--how can I set the environment variable in ubnutu ? witch files ?

---

### Post by taurus on 2009-01-24
You would set them in ~/.bashrc.

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```

---

### Post by lswb on 2009-01-24
> **taurus said:**
> You would set them in ~/.bashrc.


.bashrc for user environment varialbles and if you need to set a system-wide variable for all users and processes put it in /etc/environment.

---

### Post by mathfeel on 2009-09-16
> **lswb said:**
> .bashrc for user environment varialbles and if you need to set a system-wide variable for all users and processes put it in /etc/environment.

I cannot figure out where is this file sourced. grep yeidls several possible places depending on runlevel:
```
init.d/gdm:elif [ -r /etc/environment ]; then
init.d/gdm:  . /etc/environment
init.d/console-screen.sh:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
init.d/cron:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
pam.d/login:# parsing /etc/environment needs "readenv=1"
pam.d/login:# reading this file *in addition to /etc/environment* does not hurt
pam.d/su:# parsing /etc/environment needs "readenv=1"
pam.d/su:# reading this file *in addition to /etc/environment* does not hurt
rc0.d/K01gdm:elif [ -r /etc/environment ]; then
rc0.d/K01gdm:  . /etc/environment
rc1.d/K11cron:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
rc1.d/K01gdm:elif [ -r /etc/environment ]; then
rc1.d/K01gdm:  . /etc/environment
rc2.d/S89cron:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
rc2.d/S30gdm:elif [ -r /etc/environment ]; then
rc2.d/S30gdm:  . /etc/environment
rc3.d/S89cron:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
rc3.d/S30gdm:elif [ -r /etc/environment ]; then
rc3.d/S30gdm:  . /etc/environment
rc4.d/S89cron:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
rc4.d/S30gdm:elif [ -r /etc/environment ]; then
rc4.d/S30gdm:  . /etc/environment
rc5.d/S89cron:    [ -r /etc/environment ] && ENV_FILE="/etc/environment"
rc5.d/S30gdm:elif [ -r /etc/environment ]; then
rc5.d/S30gdm:  . /etc/environment
rc6.d/K01gdm:elif [ -r /etc/environment ]; then
rc6.d/K01gdm:  . /etc/environment
rcS.d/S90console-screen.sh:    [ -r /etc/environment ] && ENV_FILE="/etc/environment
```
I don't want to reboot just to add an entry. This information should be part of the documentation.

---

