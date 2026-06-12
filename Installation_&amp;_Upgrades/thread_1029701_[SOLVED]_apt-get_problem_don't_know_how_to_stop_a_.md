---
title: "[SOLVED] apt-get problem: don't know how to stop a sudo command"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by colbobs on 2009-01-03
[B] Ubuntu / Kubunto8.04 Acer Aspire 1640      Related to another thread regarding bluetooth, I ran through a number of suggestions, one of which was to get ndiswrapper to see if it could tell me anything useful (to be honest I was grabbing at straws and have probably got myself in a bit of a mess).

So in konsole:[/B]


colbobs@colbobs-laptop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
colbobs@colbobs-laptop:~$ sudo apt-get install ndiswrapper-common
[sudo] password for colbobs:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  opensync-module-python python-libxslt1 libmp4v2-0 jabber libgnet2.0-0 libaccess-bridge-java python-rtfcomp libamrnb3 libamrwb3 python-tz recode python-dateutil libmozjs0d
  python-opensync jabber-common librtfcomp0 convmv
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.4kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Media Change: Please insert the disc labelled
 ‘Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)’
in the drive ‘/cdrom/’ and press enter


[B]This implies to me that I'm stuck in this process until I put the disc in.  The disc is about but I don't have it to hand.

I've then run another command and it tells me that the apt-get process from earlier has locked up access.[/B]

Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_GB
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [5999B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Fetched 6189B in 0s (7490B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


**So I use system monitor to close apt-get and get no-where.**

**Errors of the newbie aside, how can I kill this process off.  I'm currently unable to run synaptec package manager because of:**

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.

I need to be able close package management applications in some other way than hat I've already done.

Need help!
Thanks in advance.
Col

---

### Post by gettinoriginal on 2009-01-03
I am in Ubuntu, so it might be different in Kubuntu (never used it) System > Admin > System Monitor > Processes, and kill whatever you need to

---

### Post by colbobs on 2009-01-03
{\QUOTE]
**So I use system monitor to close apt-get and get no-where.**

**Errors of the newbie aside, how can I kill this process off.  I'm currently unable to run synaptec package manager because of:**

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) isalready running. Please close that application first.

I need to be able close package management applications in some other way than hat I've already done.

[/QUOTE]

So I'm afraid I'd already tried it.  I tried it again anyway and to be hoest apt-get and aptitude are not to be seen running (asleep or otherwise)

---

### Post by rgrig on 2009-01-03
Try

```
sudo killall -9 apt-get
sudo rm /var/lib/dpkg/lock
```

---

### Post by colbobs on 2009-01-03
> **rgrig said:**
> Try

```
sudo killall -9 apt-get
sudo rm /var/lib/dpkg/lock
```
That did it!
Thanks rgrig.
Solved!

---

### Post by Gotlieb on 2011-04-18
Hi,

I got the same error (its driving me crazy) and I tried what you recommended but this happened 

(Q)

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What must I do next? I can not find it in system tasks.

Thanks to any help :confused:

---

### Post by onix on 2012-11-07
You must do exactly what  it tels you to do :)  

> run 'sudo dpkg --configure -a'


```
 sudo dpkg --configure -a
```


...thx guys got same problem, post helped me too

---

