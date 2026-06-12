---
title: "Partial Upgrade Problem"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by thestig_992 on 2009-09-04
Recently, every time i have tried to update my 9.04 pc, i get a message popping up saying that some things didnt upgrade properly when i upgraded from 8.10 to 9.04. When I select partial upgrade, after a while, i get this error message...

[[IMG]http://img154.imageshack.us/img154/8562/83473829.th.png[/IMG]](http://img154.imageshack.us/i/83473829.png/)

How do I fix this?

---

### Post by Partyboi2 on 2009-09-05
Hi, can you open a terminal and post the output to
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

---

### Post by thestig_992 on 2009-09-05
I know I have a lot of repositries, its pretty messed up since a lot of them were disabled when i upgraded. 

this is from apt-get update
```
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_AU
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_AU
Get:1 http://download.virtualbox.org jaunty Release.gpg [197B]
Ign http://download.virtualbox.org jaunty/non-free Translation-en_AU
Get:2 http://dl.google.com stable Release.gpg [189B]
Ign http://linux.getdropbox.com jaunty Release.gpg
Ign http://linux.getdropbox.com jaunty/main Translation-en_AU
Ign http://dl.google.com stable/non-free Translation-en_AU
Get:3 http://download.virtualbox.org jaunty Release [3454B]
Ign http://download.virtualbox.org jaunty Release
Ign http://download.skype.com stable Release.gpg
Get:4 http://wine.budgetdedicated.com jaunty Release.gpg [189B]
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_AU
Ign http://deb.playonlinux.com jaunty Release.gpg
Ign http://deb.playonlinux.com jaunty/main Translation-en_AU
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_AU
Hit http://archive.canonical.com jaunty-backports Release.gpg
Hit http://download.virtualbox.org jaunty/non-free Packages
Ign http://linux.getdropbox.com jaunty Release
Get:5 http://repository.cairo-dock.org jaunty Release.gpg [197B]
Ign http://repository.cairo-dock.org jaunty/cairo-docky Translation-en_AU
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_AU
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_AU
Hit http://archive.ubuntu.com jaunty Release.gpg
Hit http://archive.ubuntu.com jaunty/main Translation-en_AU
Get:6 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:7 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://download.skype.com stable/non-free Translation-en_AU
Ign http://linux.getdropbox.com jaunty/main Packages
Get:8 http://dl.google.com stable Release [2540B]
Ign http://dl.google.com stable Release
Get:9 http://wine.budgetdedicated.com jaunty Release [1019B]
Ign http://wine.budgetdedicated.com jaunty Release
Get:10 http://deb.playonlinux.com jaunty Release [1723B]
Ign http://archive.canonical.com jaunty-backports/partner Translation-en_AU
Hit http://archive.canonical.com jaunty-updates Release.gpg
Ign http://archive.canonical.com jaunty-updates/partner Translation-en_AU
Hit http://archive.canonical.com jaunty-security Release.gpg
Ign http://archive.canonical.com jaunty-security/partner Translation-en_AU
Hit http://archive.canonical.com jaunty-proposed Release.gpg
Ign http://archive.canonical.com jaunty-proposed/partner Translation-en_AU
Hit http://archive.canonical.com jaunty Release
Get:11 http://repository.cairo-dock.org jaunty Release [2855B]
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_AU
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com jaunty-proposed Release.gpg
Ign http://security.ubuntu.com jaunty-proposed/main Translation-en_AU
Ign http://security.ubuntu.com jaunty-proposed/restricted Translation-en_AU
Ign http://security.ubuntu.com jaunty-proposed/universe Translation-en_AU
Ign http://security.ubuntu.com jaunty-proposed/multiverse Translation-en_AU
Ign http://repository.cairo-dock.org jaunty Release
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_AU
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_AU
Ign http://archive.ubuntu.com jaunty/universe Translation-en_AU
Hit http://archive.ubuntu.com jaunty-backports Release.gpg
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_AU
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_AU
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_AU
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_AU
Hit http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://download.skype.com stable Release
Hit http://security.ubuntu.com jaunty-security Release
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:12 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:13 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:14 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:15 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Hit http://linux.getdropbox.com jaunty/main Packages
Ign http://wine.budgetdedicated.com jaunty/main Packages
Ign http://deb.playonlinux.com jaunty/main Packages
Hit http://download.skype.com stable/non-free Packages
Hit http://archive.canonical.com jaunty-backports Release
Hit http://archive.canonical.com jaunty-updates Release
Hit http://archive.canonical.com jaunty-security Release
Hit http://archive.canonical.com jaunty-proposed Release
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_AU
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_AU
Ign http://repository.cairo-dock.org jaunty/cairo-docky Packages
Hit http://security.ubuntu.com jaunty-proposed Release
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_AU
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_AU
Hit http://archive.ubuntu.com jaunty Release
Get:16 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:17 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:18 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:19 http://ppa.launchpad.net jaunty Release.gpg [307B]
Get:20 http://dl.google.com stable/non-free Packages [1010B]
Hit http://wine.budgetdedicated.com jaunty/main Packages
Hit http://deb.playonlinux.com jaunty/main Packages
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://archive.ubuntu.com jaunty-backports Release
Ign http://repository.cairo-dock.org jaunty/cairo-docky Packages
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-updates Release
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:21 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:22 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://archive.canonical.com jaunty-backports/partner Packages
Ign http://archive.canonical.com jaunty-backports/partner Sources
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/main Sources
Err http://repository.cairo-dock.org jaunty/cairo-docky Packages
  404 Not Found
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://security.ubuntu.com jaunty-proposed/main Packages
Hit http://security.ubuntu.com jaunty-proposed/restricted Packages
Hit http://security.ubuntu.com jaunty-proposed/universe Packages
Hit http://security.ubuntu.com jaunty-proposed/multiverse Packages
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:23 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:24 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:25 http://ppa.launchpad.net jaunty Release.gpg [307B]
Get:26 ftp://ftp.mysql.com binary/ Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Ign http://archive.canonical.com jaunty-updates/partner Packages
Ign http://archive.canonical.com jaunty-updates/partner Sources
Ign http://archive.canonical.com jaunty-security/partner Packages
Ign http://archive.canonical.com jaunty-security/partner Sources
Ign http://archive.canonical.com jaunty-proposed/partner Packages
Ign http://archive.canonical.com jaunty-proposed/partner Sources
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty-backports/main Packages
Hit http://archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://archive.ubuntu.com jaunty-backports/universe Packages
Hit http://archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://archive.ubuntu.com jaunty-backports/main Sources
Hit http://security.ubuntu.com jaunty-proposed/main Sources
Hit http://security.ubuntu.com jaunty-proposed/restricted Sources
Hit http://security.ubuntu.com jaunty-proposed/universe Sources
Hit http://security.ubuntu.com jaunty-proposed/multiverse Sources
Hit http://archive.ubuntu.com jaunty-backports/restricted Sources
Hit http://archive.ubuntu.com jaunty-backports/universe Sources
Hit http://archive.ubuntu.com jaunty-backports/multiverse Sources
Get:27 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Hit http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_AU
Get:28 http://ppa.launchpad.net jaunty Release [52.9kB]
Get:29 http://ppa.launchpad.net jaunty Release [74.7kB]
Get:30 http://ppa.launchpad.net jaunty Release [74.6kB]
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Get:31 http://ppa.launchpad.net jaunty Release [74.6kB]
Get:32 http://ppa.launchpad.net jaunty Release [52.9kB]
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Get:33 http://ppa.launchpad.net jaunty Release [74.6kB]
Ign http://ppa.launchpad.net jaunty Release
Hit http://archive.canonical.com jaunty-backports/partner Packages
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Get:34 http://ppa.launchpad.net jaunty Release [74.6kB]
Ign http://ppa.launchpad.net jaunty Release
Get:35 http://ppa.launchpad.net jaunty Release [74.6kB]
Get:36 http://ppa.launchpad.net jaunty Release [74.6kB]
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Get:37 http://ppa.launchpad.net jaunty Release [74.7kB]
Ign http://ppa.launchpad.net jaunty Release
Hit http://archive.canonical.com jaunty-backports/partner Sources
Hit http://archive.canonical.com jaunty-updates/partner Packages
Hit http://archive.canonical.com jaunty-updates/partner Sources
Hit http://archive.canonical.com jaunty-security/partner Packages
Hit http://archive.canonical.com jaunty-security/partner Sources
Hit http://archive.canonical.com jaunty-proposed/partner Packages
Get:38 http://ppa.launchpad.net jaunty Release [74.7kB]
Get:39 http://ppa.launchpad.net jaunty Release [74.7kB]
Get:40 http://ppa.launchpad.net jaunty Release [74.7kB]
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Ign ftp://ftp.mysql.com binary/ Release.gpg
Get:41 http://ppa.launchpad.net jaunty Release [74.6kB]
Ign http://ppa.launchpad.net jaunty Release
Get:42 http://ppa.launchpad.net jaunty Release [74.6kB]
Ign http://ppa.launchpad.net jaunty Release
Get:43 http://ppa.launchpad.net jaunty Release [74.7kB]
Hit http://ppa.launchpad.net jaunty Release
Ign http://ppa.launchpad.net jaunty Release
Hit http://archive.canonical.com jaunty-proposed/partner Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Ign http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Get:44 ftp://ftp.mysql.com binary/ Translation-en_AU
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Packages
Ign ftp://ftp.mysql.com binary/ Translation-en_AU
Get:45 http://deb.opera.com lenny Release.gpg [189B]
Ign http://deb.opera.com lenny/non-free Translation-en_AU
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_AU
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_AU
Get:46 ftp://ftp.mysql.com source/ Release.gpg
Hit http://packages.medibuntu.org jaunty Release
Get:47 http://deb.opera.com lenny Release [1067B]
Ign http://deb.opera.com lenny Release
Hit http://packages.medibuntu.org jaunty/free Packages
Ign http://deb.opera.com lenny/non-free Packages
Ign ftp://ftp.mysql.com source/ Release.gpg
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://packages.medibuntu.org jaunty/free Sources
Hit http://packages.medibuntu.org jaunty/non-free Sources
Hit http://deb.opera.com lenny/non-free Packages
Get:48 ftp://ftp.mysql.com binary/ Release
Ign ftp://ftp.mysql.com binary/ Release
Get:49 ftp://ftp.mysql.com source/ Release
Ign ftp://ftp.mysql.com source/ Release
Get:50 ftp://ftp.mysql.com binary/ Packages
Ign ftp://ftp.mysql.com binary/ Packages
Get:51 ftp://ftp.mysql.com source/ Sources
Ign ftp://ftp.mysql.com source/ Sources
Get:52 ftp://ftp.mysql.com binary/ Packages
Ign ftp://ftp.mysql.com binary/ Packages
Get:53 ftp://ftp.mysql.com source/ Sources
Ign ftp://ftp.mysql.com source/ Sources
Get:54 ftp://ftp.mysql.com binary/ Packages
Err ftp://ftp.mysql.com binary/ Packages
  Unable to fetch file, server said 'Failed to open file.  '
Get:55 ftp://ftp.mysql.com source/ Sources
Err ftp://ftp.mysql.com source/ Sources
  Unable to fetch file, server said 'Failed to open file.  '
Fetched 9444B in 20s (458B/s)
```

apt-get dist-upgrade was too long to post the output of, but it seemed to do a partial upgrade...If i have the same error next time it tries to update, then ill reactivate this thread, but otherwise the dist-upgrade command seems to have fixed it, thanks

---

