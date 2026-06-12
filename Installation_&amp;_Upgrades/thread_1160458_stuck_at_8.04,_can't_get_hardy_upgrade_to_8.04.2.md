---
title: "stuck at 8.04, can't get hardy upgrade to 8.04.2"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by nmsmith on 2009-05-15
I recently found several intrepid packages on my system, as I had added a repository that I shouldn't have. I have now sorted this by 'pinning' my version and doing lots of stressful downgrading. Everything now appears to be vanilla hardy, including Firefox 3 beta 5 for example.

```
user@box:~$ cat /etc/issue
Ubuntu 8.04 \n \l

```

```
user@box:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

```

I have now restored my sources:

```
user@box:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

# medibuntu
deb http://packages.medibuntu.org/ hardy free non-free

# mythexport
deb http://ppa.launchpad.net/mythbuntu-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/mythbuntu-testing/ubuntu hardy main
```

Can anyone tell me how to upgrade to 8.04.2 without simply moving to intrepid/jaunty?

---

### Post by zvacet on 2009-05-16
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If you get all updates you should be using 8.04.2.

---

### Post by nmsmith on 2009-05-16
This features long swathes of code. Sorry.

```
user@box:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for nick: 
Hit http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_GB                      
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                 
Hit http://gb.archive.ubuntu.com hardy Release.gpg                             
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB                  
Get: 1 http://security.ubuntu.com hardy-security Release.gpg [189B]            
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB           
Hit http://ppa.launchpad.net hardy Release                                     
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB            
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB  
Get: 2 http://gb.archive.ubuntu.com hardy-updates Release.gpg [189B] 
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB   
Hit http://packages.medibuntu.org hardy Release                      
Hit http://gb.archive.ubuntu.com hardy Release                       
Get: 3 http://security.ubuntu.com hardy-security Release [58.5kB]   
Get: 4 http://gb.archive.ubuntu.com hardy-updates Release [58.5kB]      
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://packages.medibuntu.org hardy/free Packages                          
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://ppa.launchpad.net hardy/main Packages                               
Hit http://ppa.launchpad.net hardy/main Sources                                
Get: 5 http://security.ubuntu.com hardy-security/main Packages [164kB]
Hit http://gb.archive.ubuntu.com hardy/main Packages
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources 
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Get: 6 http://gb.archive.ubuntu.com hardy-updates/main Packages [435kB]
Get: 7 http://security.ubuntu.com hardy-security/restricted Packages [8008B]
Get: 8 http://security.ubuntu.com hardy-security/main Sources [27.6kB]         
Get: 9 http://security.ubuntu.com hardy-security/restricted Sources [903B]     
Get: 10 http://security.ubuntu.com hardy-security/universe Packages [82.6kB]   
Get: 11 http://security.ubuntu.com hardy-security/universe Sources [12.9kB]    
Get: 12 http://security.ubuntu.com hardy-security/multiverse Packages [11.9kB] 
Get: 13 http://security.ubuntu.com hardy-security/multiverse Sources [1105B]   
Get: 14 http://gb.archive.ubuntu.com hardy-updates/restricted Packages [8437B]
Get: 15 http://gb.archive.ubuntu.com hardy-updates/main Sources [112kB]
Get: 16 http://gb.archive.ubuntu.com hardy-updates/restricted Sources [901B]
Get: 17 http://gb.archive.ubuntu.com hardy-updates/universe Packages [198kB]
Get: 18 http://gb.archive.ubuntu.com hardy-updates/universe Sources [42.5kB]
Get: 19 http://gb.archive.ubuntu.com hardy-updates/multiverse Packages [29.1kB]
Get: 20 http://gb.archive.ubuntu.com hardy-updates/multiverse Sources [5538B]
Fetched 1258kB in 2s (492kB/s)                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
user@box:~$ 
```

It always bugs me when you don't get told which packages are not being upgraded...

```
user@box:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  mplayer
The following packages will be DOWNGRADED:
  libpango1.0-0 libpango1.0-common
0 upgraded, 0 newly installed, 2 downgraded, 1 to remove and 0 not upgraded.
Need to get 347kB of archives.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com hardy/main libpango1.0-0 1.20.1-1 [284kB]
Get: 2 http://gb.archive.ubuntu.com hardy/main libpango1.0-common 1.20.1-1 [62.9kB]
Fetched 347kB in 0s (573kB/s)           
(Reading database ... 125989 files and directories currently installed.)
Removing mplayer ...
dpkg - warning: downgrading libpango1.0-0 from 1.20.5-0ubuntu1.1 to 1.20.1-1.
(Reading database ... 125920 files and directories currently installed.)
Preparing to replace libpango1.0-0 1.20.5-0ubuntu1.1 (using .../libpango1.0-0_1.20.1-1_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
dpkg - warning: downgrading libpango1.0-common from 1.20.5-0ubuntu1.1 to 1.20.1-1.
Preparing to replace libpango1.0-common 1.20.5-0ubuntu1.1 (using .../libpango1.0-common_1.20.1-1_all.deb) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Unpacking replacement libpango1.0-common ...
Setting up libpango1.0-common (1.20.1-1) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Updating font configuration of pango...
Cleaning up category xfont..
Updating category xfont..

Setting up libpango1.0-0 (1.20.1-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
user@box:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@box:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
```
user@box:~$ cat /etc/issue
Ubuntu 8.04 \n \l

user@box:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy
user@box:~$ 

```

That feels disappointing.

---

### Post by nmsmith on 2009-05-23
bump

---

### Post by liddokun10 on 2009-06-27
yeah i also have this issue problem.

cat /etc/issue tells me i'm at 8.04.2 \n \1

but

cat /boot/grub/menu.lst shows

Ubuntu 8.04.1, kernel 2.6.24-19-generic

which do i trust? lol :D

---

### Post by snowpine on 2009-06-27
8.04.2 = 8.04 with all current updates applied
Nothing to worry about.

---

