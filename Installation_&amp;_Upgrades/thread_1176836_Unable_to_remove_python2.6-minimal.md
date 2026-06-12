---
title: "Unable to remove python2.6-minimal"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by waltm on 2009-06-02
I've been having issues installing any new updates since I last upgraded my system and they seem to be related to python2.6-minimal errors.

I found some info on replacing that package by running 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

but even that gives the following error
```

Setting up python2.6-minimal (2.6.2-0ubuntu1) ...
update-binfmts: unable to open /var/lib/binfmts: No such file or directory 
dpkg: error processing python2.6-minimal (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.6-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Synaptic will not let me remove it either.

Does anyone have any ideas on how to either get rid or this or upgrade?

---

### Post by waltm on 2009-06-05
Is there another forum where this question might be more appropriate?

---

### Post by waltm on 2009-06-07
I'm having issues with other packages as well as package maintanence, such as "apt-get autoremove" wich returns the error 
```
htpc@htpc-desktop:~$ sudo apt-get autoremove
[sudo] password for htpc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  mythbuntu-desktop: Depends: notify-osd but it is not installed
E: Unmet dependencies. Try using -f.
htpc@htpc-desktop:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-numeric libglide2 python-xml xutils-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  notify-osd
The following NEW packages will be installed:
  notify-osd
0 upgraded, 1 newly installed, 0 to remove and 639 not upgraded.
5 not fully installed or removed.
Need to get 0B/146kB of archives.
After this operation, 799kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140581 files and directories currently installed.)
Unpacking notify-osd (from .../notify-osd_0.9.11-0ubuntu3_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd' with
  different file `/usr/share/dbus-1/services/org.freedesktop.Notifications.service', not allowed
dpkg: error processing /var/cache/apt/archives/notify-osd_0.9.11-0ubuntu3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/notify-osd_0.9.11-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
htpc@htpc-desktop:~$ 

```

I am able to upgrade some things in synaptic if I choose to do them individually but when I try to upgrade all it usually exits with an error such as this one when I tried to repair the broken package mythbuntu-desktop
```
E: /var/cache/apt/archives/notify-osd_0.9.11-0ubuntu3_i386.deb: subprocess pre-installation script returned error exit status 2

```

I tried deleting the archive and re-installing but with the same error.


Any guidance as to where to look for clues would be greatly appreciated.

---

