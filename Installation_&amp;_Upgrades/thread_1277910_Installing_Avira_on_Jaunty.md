---
title: "Installing Avira on Jaunty"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Wesely-C on 2009-09-28
I'm trying to install Avira Antivir on my Jaunty installation, and though I did find a reference at [http://ubuntuforums.org/showthread.php?t=430920](http://ubuntuforums.org/showthread.php?t=430920) to instructions from this URL:

[http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php](http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php)

Unfortunatly, these instuctions have lead to a dead end, as shown by my terminal output here:

```
jwesleycooper@jwesleycooper-laptop:~$ wget http://dazuko.org/files/dazuko-source_2.1.0-1_all.deb
--2009-09-28 18:47:03--  http://dazuko.org/files/dazuko-source_2.1.0-1_all.deb
Resolving dazuko.org... 82.165.105.216
Connecting to dazuko.org|82.165.105.216|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 178478 (174K) [application/x-debian-package]
Saving to: `dazuko-source_2.1.0-1_all.deb'

100%[======================================>] 178,478     76.0K/s   in 2.3s    

2009-09-28 18:47:06 (76.0 KB/s) - `dazuko-source_2.1.0-1_all.deb' saved [178478/178478]

jwesleycooper@jwesleycooper-laptop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for jwesleycooper: 
jwesleycooper@jwesleycooper-laptop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com jaunty-security Release [49.6kB]
Hit http://us.archive.ubuntu.com jaunty Release
Get:4 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]        
Get:5 http://security.ubuntu.com jaunty-security/main Packages [104kB]        
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Get:6 http://us.archive.ubuntu.com jaunty-updates/main Packages [180kB]
Get:7 http://security.ubuntu.com jaunty-security/restricted Packages [2589B]
Get:8 http://security.ubuntu.com jaunty-security/main Sources [26.9kB]      
Get:9 http://us.archive.ubuntu.com jaunty-updates/restricted Packages [2589B]  
Get:10 http://us.archive.ubuntu.com jaunty-updates/main Sources [51.3kB]      
Get:11 http://security.ubuntu.com jaunty-security/restricted Sources [623B]    
Get:12 http://security.ubuntu.com jaunty-security/universe Packages [35.9kB]   
Get:13 http://us.archive.ubuntu.com jaunty-updates/restricted Sources [623B]   
Get:14 http://us.archive.ubuntu.com jaunty-updates/universe Packages [56.7kB]
Get:15 http://us.archive.ubuntu.com jaunty-updates/universe Sources [15.3kB]   
Get:16 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [8128B] 
Get:17 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [2505B]  
Get:18 http://security.ubuntu.com jaunty-security/universe Sources [7109B]     
Get:19 http://security.ubuntu.com jaunty-security/multiverse Packages [1662B]
Get:20 http://security.ubuntu.com jaunty-security/multiverse Sources [588B]
Fetched 596kB in 3s (153kB/s)                  
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com jaunty/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
jwesleycooper@jwesleycooper-laptop:~$ sudo apt-get install module-assistant debhelper j2re1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package j2re1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.4 has no installation candidate
jwesleycooper@jwesleycooper-laptop:~$ sudo apt-get install module-assistant debhelper j2re1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package j2re1.5 has no installation candidate
jwesleycooper@jwesleycooper-laptop:~$ sudo apt-get install module-assistant debhelper j2re1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package j2re1.6
jwesleycooper@jwesleycooper-laptop:~$ 

```...anyone know how to actually install this?

---

