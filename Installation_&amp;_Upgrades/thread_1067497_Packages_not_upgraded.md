---
title: "Packages not upgraded"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by mk4mzid on 2009-02-11
Sorry for the noob question, but when I install a pkg, why are so many shown as 'not upgraded'?

root@myserver:~# apt-get install gtkpod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mp3gain recode
The following NEW packages will be installed:
  gtkpod
0 upgraded, 1 newly installed, 0 to remove and **106 not upgraded.**
Need to get 712kB of archives.
After unpacking 2683kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe gtkpod 0.99.10-2 [712kB]
Fetched 712kB in 4s (144kB/s)  
Selecting previously deselected package gtkpod.
(Reading database ... 103594 files and directories currently installed.)
Unpacking gtkpod (from .../gtkpod_0.99.10-2_i386.deb) ...
Setting up gtkpod (0.99.10-2) ...

root@myserver:~#

Tnx

---

### Post by avtolle on 2009-02-11
I don't know, but suspect that there are 106 upgrades available to your system. You directed the installation of only one specific package. I don't know how you have set up the notification of upgrades on your system, or more precisely, how often you have directed the upgrade manager to check; I've mine set to check daily.

If you want to take a look, run in terminal ```
sudo aptitude update
```which, if you are running 8.10, will, after it does its thing, tell you how many updates are available.

---

### Post by mk4mzid on 2009-02-11
Well typically I use Synaptic. I'll search and find the pkg I want, check it, and then apply. It does the same thing, tells me 1 pkg will be installed and under 'unchanged' there are the 106 pkgs.
I started Update Manager and it tells me I can install 111 updates. Guess I'm a little fuzzy on updates vs the pkgs it lists under the 'unchanged' list in Synaptic.

Also ran aptitude upgrade as suggested, but looks like that's just a list of my repositories right?

```
root@myserver:~# aptitude update
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [189B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US        
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US               
Get:3 http://packages.medibuntu.org gutsy Release.gpg [197B]
Ign http://packages.medibuntu.org gutsy/free Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US   
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US 
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [189B] 
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US                        
Hit http://packages.medibuntu.org gutsy Release                      
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://us.archive.ubuntu.com gutsy-updates Release
Hit http://packages.medibuntu.org gutsy/free Packages                
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://us.archive.ubuntu.com gutsy/universe Packages             
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://packages.medibuntu.org gutsy/non-free Packages            
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 4B in 1s (3B/s)  
Reading package lists... Done
root@myserver:~#
```

I'm going to go ahead and apply the 111 updates that Update Manager has listed and report back.

Thanks for your assistance.

---

### Post by mk4mzid on 2009-02-14
Ok, I get it now. When I use Synaptic or apt-get and it tells me there are x pkgs that will not be installed, those are updates.
I applied the 111 updates as previously stated. I just installed another pkg and it said 1 would not be installed, which was mplayer. Checked update manager and there's 1 update listed...for mplayer. I understand now.
I never claimed to be the sharpest knife in the drawer!

---

