---
title: "Update Manager unable to detect the availability of new release (8.10)"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by ajaygautam on 2008-12-30
I am trying to upgrade my desktop from 8.04 to 8.10.
(Ubuntu is running in Virtual Box on a win xp host)

Problem:
Update Manager unable to detect the availability of new release (8.10)

I am following steps from:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

My Steps (appropriate screen-shots captured and attached):

1. System -> About Ubuntu: Says "...interest in Ubuntu 8.04 - the Hardy Heron - released..."
2. System -> Administration -> Software Sources: Make sure "Show new distribution releases" is set to "Normal releases"
3. System -> Administration -> Update Manager
--- a. Click "Check"
--- b. Install all available updates
--- c. Click "Check" again
--- d. Update manager says: "Your system is up-to-date".
4. hmm....
5. Reboot
6. System -> Administration -> Update Manager
--- a. Click "Check"
--- b. Update manager says: "Your system is up-to-date".

Can't get update manager to recognize 8.10.

Any help / pointers in right direction would be highly appreciated.

Thanks

Ajay :( :confused:

---

### Post by gettinoriginal on 2008-12-30
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

---

### Post by ajaygautam on 2008-12-30
> **gettinoriginal said:**
> ```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

That does not work either:
```

root@gautaag-desktop:~# apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg          
Hit http://us.archive.ubuntu.com hardy Release.gpg                                              
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                                   
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com hardy-security Release                       
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://security.ubuntu.com hardy-security/restricted Packages           
Hit http://us.archive.ubuntu.com hardy-updates Release                                           
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources                                 
Hit http://security.ubuntu.com hardy-security/universe Packages             
Hit http://security.ubuntu.com hardy-security/universe Sources              
Hit http://security.ubuntu.com hardy-security/multiverse Packages           
Hit http://security.ubuntu.com hardy-security/multiverse Sources            
Get:1 http://us.archive.ubuntu.com hardy/main Packages [1178kB]             
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Get:2 http://us.archive.ubuntu.com hardy/universe Packages [4293kB]
Get:3 http://us.archive.ubuntu.com hardy/universe Sources [1323kB]                                                                                                                
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                                                                                                                        
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                                                                                                                         
Hit http://us.archive.ubuntu.com hardy-updates/main Packages                                                                                                                      
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages                                                                                                                
Hit http://us.archive.ubuntu.com hardy-updates/main Sources                                                                                                                       
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources                                                                                                                 
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages                                                                                                                  
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                                                                                                                   
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages                                                                                                                
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources                                                                                                                 
Fetched 6794kB in 47s (143kB/s)                                                                                                                                                   
Reading package lists... Done

```
```

root@gautaag-desktop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

other info:
```

root@gautaag-desktop:~# uname -a
Linux gautaag-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

root@gautaag-desktop:~# cat /etc/issue
Ubuntu 8.04.1 \n \l

root@gautaag-desktop:~# cat /proc/version
Linux version 2.6.24-22-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 18:32:42 UTC 2008


```

Any other suggestions ?

Thanks

Ajay

---

### Post by GrandpaLeaman on 2008-12-30
Go into Software Sources and see if you have "LTS Upgrades Only" selected (I'm at work on a windows machine, so I'm going by memory).
 
Hope this helps!

---

### Post by gettinoriginal on 2008-12-30
as 8.10 is not a LTS, you want to have it set to Normal Releases

---

### Post by stderr on 2008-12-30
He says he's already checked the LTS/normal setting, and his screenshot verifies that. 

Goodness knows what's wrong... there's nothing else that I can think of to try :|

edit: it might be an idea to verify that setting with

```
cat /etc/update-manager/release-upgrades
```

The last line should read 

```
Prompt=normal
```

edit2: And I see you have the 8.10 CD or CD image too. Have you tried using that to upgrade directly? (e.g. executing the cdromupgrade binary in the CD directory)

---

### Post by ajaygautam on 2008-12-31
> **stderr said:**
> He says he's already checked the LTS/normal setting, and his screenshot verifies that. 

Goodness knows what's wrong... there's nothing else that I can think of to try :|

edit: it might be an idea to verify that setting with

```
cat /etc/update-manager/release-upgrades
```

The last line should read 

```
Prompt=normal
```

edit2: And I see you have the 8.10 CD or CD image too. Have you tried using that to upgrade directly? (e.g. executing the cdromupgrade binary in the CD directory)

```

cat /etc/update-manager/release-upgrades

# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
prompt=normal

```

The cd you see is not the upgrade cd. It does not have cdromupgrade binary :(

Perhaps I should download the upgrade cd and try with that.

Please let me know if you have anything else I could try...

Thanks

Ajay

---

