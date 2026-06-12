---
title: "Could not install any package un ubuntu 9.10"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by friendsforravi on 2009-11-01
Hi I could not install any Package in ubuntu 9.10.

I am getting below error message.

ravi@ravi-desktop:~$ sudo apt-get install d4x
[sudo] password for ravi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
d4x is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
ravi@ravi-desktop:~$ 

I have tried these also but no use

ravi@ravi-desktop:~$ sudo aptitude update
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-security/multiverse Sources
Reading package lists... Done

ravi@ravi-desktop:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  gnome-app-install 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ravi@ravi-desktop:~$ sudo apt-get remove --purge d4x
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  d4x*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,077kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142795 files and directories currently installed.)
Removing d4x ...
Purging configuration files for d4x ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
ravi@ravi-desktop:~$

---

### Post by Turtle.net on 2009-11-01
You can maybe try a ```
sudo apt-get autoremove
``` that will remove all unnecessary package, an other solution could be ```
sudo dpkg-reconfigure gnome-app-install
```

Anyway, these commands cannot hurt.

If there is an error please post the result of these commands.

---

### Post by friendsforravi on 2009-11-01
Hey.. I have tried the commands, I think it is not yet resolved

Please see below and help me. I am desperate, I could not do anything.

ravi@ravi-desktop:~$ sudo apt-get autoremove
[sudo] password for ravi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
ravi@ravi-desktop:~$ sudo dpkg-reconfigure gnome-app-install
/usr/sbin/dpkg-reconfigure: gnome-app-install is broken or not fully installed
ravi@ravi-desktop:~$

---

### Post by friendsforravi on 2009-11-01
> **Turtle.net said:**
> You can maybe try a ```
sudo apt-get autoremove
``` that will remove all unnecessary package, an other solution could be ```
sudo dpkg-reconfigure gnome-app-install
```

Anyway, these commands cannot hurt.

If there is an error please post the result of these commands.

Hey.. I have tried the commands, I think it is not yet resolved

Please see below and help me. I am desperate, I could not do anything.

ravi@ravi-desktop:~$ sudo apt-get autoremove
[sudo] password for ravi:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
ravi@ravi-desktop:~$ sudo dpkg-reconfigure gnome-app-install
/usr/sbin/dpkg-reconfigure: gnome-app-install is broken or not fully installed
ravi@ravi-desktop:~$

---

### Post by Turtle.net on 2009-11-01
you could try this ```
dpkg --configure -a
apt-get -f install
```

And through synaptic, can you remove gnome-app-install ?
What do youhave in synaptic under Broken packages ?

---

### Post by friendsforravi on 2009-11-02
No use please see below

ravi@ravi-desktop:~$ sudo dpkg --configure -a
ravi@ravi-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-app-install (0.5.60.1ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing gnome-app-install (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Turtle.net on 2009-11-02
two things
{CODE]sudo apt-get remove gnome-app-install[/CODE]
and verify that you have enough space on each partition (using nautilus for instance)

---

### Post by Niniel on 2009-11-02
I was able to install software through the software center, but it won't work via Synaptic (getting an error about some temp directory). 
Very strange.

---

### Post by friendsforravi on 2009-11-03
> **Turtle.net said:**
> two things
{CODE]sudo apt-get remove gnome-app-install[/CODE]
and verify that you have enough space on each partition (using nautilus for instance)

Please see the below error message. I have almost 14.7 GB of free space in Filesystem.

:(:(:(
i@ravi-desktop:~$ sudo apt-get remove gnome-app-install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-app-install
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,884kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142766 files and directories currently installed.)
Removing gnome-app-install ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing gnome-app-install (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-app-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
ravi@ravi-desktop:~$

---

### Post by Turtle.net on 2009-11-03
I'm out of ideas. Look at this [blog]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/"), i don't now if that will save your system, sounds like it but you'll have to do some tests ...

---

