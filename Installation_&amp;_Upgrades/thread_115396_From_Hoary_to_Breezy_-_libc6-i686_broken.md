---
title: "From Hoary to Breezy - libc6-i686 broken"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by gusenise on 2006-01-10
To install the Breezy version I junt changed my repositories config file to find the Breezy version. So I tryed to upgrade the system. It worked until the package libc6-i686!! Now it is broken and I can't install anything else because of it.

So I changed again my repositories to find Hoary version, but it didin't work out.

I am afraid I did a stupid thing. Anyone, please help me with that??!!
Thanks in advance!!

---

### Post by Perfect Storm on 2006-01-10
What does it specific says?
```
sudo apt-get check
```

Can you reinstall it?
```
sudo apt-get autoclean
sudo apt-get remove libc6-i686
sudo apt-get install libc6-i686 ubuntu-minimal

```

---

### Post by gusenise on 2006-01-10
Thank you for helping!!

>>sudo apt-get check
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.5-1ubuntu12 is installed
E: Unmet dependencies. Try using -f.

Should I run 'apt-get -f install'?

---

### Post by gusenise on 2006-01-10
It seems like there are depedencies problems...what should I do?

Setting up libc6 (2.3.5-1ubuntu12) ...
Checking for services that may need to be restarted...head: `-1' option is obsolete; use `-n 1'
Try `head --help' for more information.
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.3.5-1ubuntu12); however:
  Package libc6 is not configured yet.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on glibc-2.3.5-0ubuntu1; however:
  Package glibc-2.3.5-0ubuntu1 is not installed.
  Package libc6 which provides glibc-2.3.5-0ubuntu1 is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache-mod-acct-pgsql:
 libapache-mod-acct-pgsql depends on libc6 (>= 2.3.2.ds1-4); however:
  Package libc6 is not configured yet.
dpkg: error processing libapache-mod-acct-pgsql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6
 libc6-dev
 locales
 libapache-mod-acct-pgsql
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Perfect Storm on 2006-01-11
How's your sourcelist looks like?

```
sudo gedit /etc/apt/sources.list

```

---

### Post by gusenise on 2006-01-11
Here is my sources.list:

```
# deb http://non-us.debian.org/debian-non-US/ stable/non-US main contrib non-free 
# deb http://security.debian.org/ stable/updates main contrib non-free 
# Uncomment if you want the apt-get source function to work
deb-src http://http.us.debian.org/debian/ stable main contrib non-free 
# deb-src http://non-us.debian.org/debian-non-US/ stable/non-US main contrib non-free 
# deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted  

## Uncomment the following two lines to fetch updated software from the network
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
## deb http://ubuntu-backports.mirrormax.net/ breezy-backports main universe multiverse restricted
## deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted

```

---

### Post by gusenise on 2006-01-11
What kind of messenger you are using?

I am using Gaim, with an msn account: [email]gustavosenise@hotmail.com[/email]

---

