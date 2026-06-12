---
title: "Aptitude update fails: &quot;Size mismatch&quot;"
date: 2008-11-24
forum: General Help
---

### Post by explosive on 2008-11-24
I have not been able to install these updates since their release. Error message is shown in the output below.

```
tom@exp:~$ sudo aptitude update; sudo aptitude upgrade
[sudo] password for tom:
Get:1 http://archive.canonical.com gutsy Release.gpg [189B]
Ign http://archive.canonical.com gutsy/partner Translation-en_GB             
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [189B]           
Ign http://security.ubuntu.com gutsy-security/main Translation-en_GB         
Get:3 http://gb.archive.ubuntu.com gutsy Release.gpg [191B]
Hit http://gb.archive.ubuntu.com gutsy/main Translation-en_GB               
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_GB
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com gutsy-security Release
Hit http://archive.canonical.com gutsy Release 
Hit http://gb.archive.ubuntu.com gutsy/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy/multiverse Translation-en_GB
Get:4 http://gb.archive.ubuntu.com gutsy-updates Release.gpg [189B]
Ign http://gb.archive.ubuntu.com gutsy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com gutsy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com gutsy Release                     
Hit http://archive.canonical.com gutsy/partner Packages                             
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://gb.archive.ubuntu.com gutsy-updates Release
Hit http://archive.canonical.com gutsy/partner Sources                              
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://gb.archive.ubuntu.com gutsy/main Packages
Hit http://gb.archive.ubuntu.com gutsy/restricted Packages
Hit http://gb.archive.ubuntu.com gutsy/main Sources
Hit http://gb.archive.ubuntu.com gutsy/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://gb.archive.ubuntu.com gutsy/universe Packages
Hit http://gb.archive.ubuntu.com gutsy/universe Sources
Hit http://gb.archive.ubuntu.com gutsy/multiverse Packages
Hit http://gb.archive.ubuntu.com gutsy/multiverse Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/main Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/main Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 4B in 0s (12B/s) 
Reading package lists... Done
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages will be upgraded:
  hpijs hplip hplip-data 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7522kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
Get:1 http://gb.archive.ubuntu.com gutsy-updates/main hplip-data 2.7.7.dfsg.1-0ubuntu5.1 [6898kB]
Get:2 http://gb.archive.ubuntu.com gutsy-updates/main hplip 2.7.7.dfsg.1-0ubuntu5.1 [290kB]
Get:3 http://gb.archive.ubuntu.com gutsy-updates/main hpijs 2.7.7+2.7.7.dfsg.1-0ubuntu5.1 [334kB]
Fetched 7523kB in 3s (1971kB/s)
E: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb: Size mismatch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done     
```

I'm using 7.10 - any ideas?

---

### Post by swoody on 2008-11-24
Here's a couple ideas,

1) Disk full - please post the result of "df -h" here.
2) Corrupted File from Apt-get - "apt-get clean" should fix this
3) Outdated program information in aptitude - "apt-get update" should correct this.

Please let me know if any of these work :)

---

### Post by explosive on 2008-11-24
Unfortuantely none of those are causing the problem. The disk definerly isn't full, and  neither 'clean' or 'update' fix it :(

---

### Post by plucky on 2008-11-24
See this [thread](http://ubuntuforums.org/showthread.php?p=6238429#post6238429)

Good Luck

---

### Post by swoody on 2008-11-24
Plucky, you must have accidentally deleted the "h" at the beginning of that link, cause it doesn't come up right, but explosion here's the link Plucky posted:
[http://ubuntuforums.org/showthread.php?p=6238429#post6238429](http://ubuntuforums.org/showthread.php?p=6238429#post6238429)

---

