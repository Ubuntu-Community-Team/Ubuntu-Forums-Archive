---
title: "Software Sources Starts And Stops"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by VerGuy on 2009-01-18
I am using Ubuntu 8.10 and I have a problem with the updating process. I have found that I cannot specify new Software Sources or remove old ones with the Software Sources management tool. This is probably not a huge issue as I would like to get my system to a state where everything is working [I have been asked to recommend an OS to a friend who is even more MS dependant that me, never having heard of Linux!]

TIA.

---

### Post by taurus on 2009-01-18
Try synaptic, System -> Administration -> Synaptic Package Manager.

---

### Post by VerGuy on 2009-01-18
> **taurus said:**
> Try synaptic, System -> Administration -> Synaptic Package Manager.

When I try this what I get is:

"The repository information has changed. You have to click on the "Reload" button for your changes to take effect"

[See attached picture] This re-occurs if I click the reload button and if I close the Synaptic Package Manager and restart it.

---

### Post by taurus on 2009-01-18
Just close synaptic and run these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by VerGuy on 2009-01-18
> **taurus said:**
> Just close synaptic and run these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

I have just tried these and the situation is the same [unchanged]

I have also tried:

```
sudo apt-get dist-upgrade
```

In the hope that it might fix something which is broken in my system. It did not work.

---

### Post by taurus on 2009-01-18
Cam you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by VerGuy on 2009-01-18
> **taurus said:**
> Cam you post your /etc/apt/sources.list?

here is the content of that file: [It reads like another language to me!]

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# This entris allows for th install of the Opera browser
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

---

### Post by taurus on 2009-01-18
> **VerGuy said:**
> here is the content of that file: [It reads like another language to me!]

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# This entris allows for th install of the Opera browser
**[COLOR="Red"]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main[/COLOR]**
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
Any reason why you have a repo for dapper while you are obviously running intrepid?

I would recommend you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of that line to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**deb http://archive.canonical.com/ubuntu dapper-commercial main
```
Save it and close down gedit editing window.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by VerGuy on 2009-01-18
Don't know how the Dapper entries got in there. I have commented them out as you suggested and still no change. The system does still notify me about updates: It is just if I want to add a software source at some future date I may not be able to.

[Please excuse any spelling mistakes: I am typing this reply without my glasses and so I cannot be sure that what I am typing is acually what I intend to type]

---

### Post by Prot on 2009-01-18
> **VerGuy said:**
> Don't know how the Dapper entries got in there. I have commented them out as you suggested and still no change. The system does still notify me about updates: It is just if I want to add a software source at some future date I may not be able to.

[Please excuse any spelling mistakes: I am typing this reply without my glasses and so I cannot be sure that what I am typing is acually what I intend to type]

Same thing started happening to me. Linux Mint 6 (Intrepid).
I can no longer add repositories with Synaptic only manually by editing sources.plist.  :(

---

### Post by taurus on 2009-01-18
> **VerGuy said:**
> Don't know how the Dapper entries got in there. I have commented them out as you suggested and still no change. The system does still notify me about updates: It is just if I want to add a software source at some future date I may not be able to.

[Please excuse any spelling mistakes: I am typing this reply without my glasses and so I cannot be sure that what I am typing is acually what I intend to type]

Can you post the exact and complete outputs of these two commands?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by VerGuy on 2009-01-19
> **taurus said:**
> Can you post the exact and complete outputs of these two commands?

```
sudo apt-get update
sudo apt-get upgrade
```

OK. Will do. I have to restart my station to do that....

---

### Post by VerGuy on 2009-01-22
OK I finally have my machine back from my son.

Results of Commands:

sudo apt-get update

Result:

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_GB                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg [189B]        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports Release.gpg [189B]      
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Translation-en_GB
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Get: 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release [51.2kB]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_GB                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [52.3kB]     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_GB             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports Release [44.0kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1805B]
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [16.0kB]     
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [571B]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [20.7kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources                   
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages [275kB]  
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [3589B]  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1345B]
Get: 16 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B] 
Get: 17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages [5767B]
Get: 18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources [85.2kB]
Get: 19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources [1701B]
Get: 20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages [39.7kB]
Get: 21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources [9247B]
Get: 22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages [3194B]
Get: 23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B]
Get: 24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Packages [67.8kB]
Get: 25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Get: 26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Packages [21.5kB]
Get: 27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Packages [14B]
Get: 28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/main Sources [12.3kB]
Get: 29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/restricted Sources [14B]
Get: 30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/universe Sources [7588B]
Get: 31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-backports/multiverse Sources [14B]
Fetched 766kB in 4s (165kB/s)                    
Reading package lists... Done

Result of typing:

sudo apt-get upgrade

Initial response from workstation:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cheese libpoppler-glib3 libpoppler3 libv4l-0 poppler-utils xserver-xorg-video-intel
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3742kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? 

After 'Y' Response:

Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe cheese 2.24.2-0ubuntu0+intrepid1 [2404kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libpoppler3 0.8.7-1ubuntu0.1 [693kB]                                                              
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libpoppler-glib3 0.8.7-1ubuntu0.1 [64.1kB]                                                        
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main libv4l-0 0.5.7-1~intrepid1 [63.4kB]                                                               
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main poppler-utils 0.8.7-1ubuntu0.1 [79.5kB]                                                           
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main xserver-xorg-video-intel 2:2.4.1-1ubuntu10.1 [438kB]                                              
Fetched 3742kB in 14s (258kB/s)                                                                                                                             
Reading changelogs... Done
(Reading database ... 288424 files and directories currently installed.)
Preparing to replace cheese 2.24.1-0ubuntu1 (using .../cheese_2.24.2-0ubuntu0+intrepid1_amd64.deb) ...
Unpacking replacement cheese ...
Preparing to replace libpoppler3 0.8.7-1 (using .../libpoppler3_0.8.7-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libpoppler3 ...
Preparing to replace libpoppler-glib3 0.8.7-1 (using .../libpoppler-glib3_0.8.7-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libpoppler-glib3 ...
Preparing to replace libv4l-0 0.5.6-1~intrepid1 (using .../libv4l-0_0.5.7-1~intrepid1_amd64.deb) ...
Unpacking replacement libv4l-0 ...
Preparing to replace poppler-utils 0.8.7-1 (using .../poppler-utils_0.8.7-1ubuntu0.1_amd64.deb) ...
Unpacking replacement poppler-utils ...
Preparing to replace xserver-xorg-video-intel 2:2.4.1-1ubuntu10 (using .../xserver-xorg-video-intel_2%3a2.4.1-1ubuntu10.1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
Setting up cheese (2.24.2-0ubuntu0+intrepid1) ...

Setting up libpoppler3 (0.8.7-1ubuntu0.1) ...

Setting up libpoppler-glib3 (0.8.7-1ubuntu0.1) ...

Setting up libv4l-0 (0.5.7-1~intrepid1) ...

Setting up poppler-utils (0.8.7-1ubuntu0.1) ...
Setting up xserver-xorg-video-intel (2:2.4.1-1ubuntu10.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Now testing status of original problem [Software Sources]

Program asks for password and goes no further.

Synaptic Package Manager does nothing [does not crash, does not display error, does not display another dialog,...] just opens and closes.

---

### Post by taurus on 2009-01-22
Looks like you have some hardy repos in your /etc/apt/sources.list which is not a good thing.  Mixing repos can only bring you headache.

Post your /etc/apt/sources.list

```
cat /etc/apt/sources.list
```

p.s.  If you want Medibuntu, here is the right way.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by VerGuy on 2009-01-22
OK. Result of command:

cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# This entris allows for th install of the Opera browser
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

Medibuntu? Sounds interesting and I would like to know more. But as an absolute Ubuntu beginner I am not even sure what I am interested in [you probably guessed that by now!]

While we are on the subject of what-is-what what is Mythbuntu? or TVBuntu? I get that *'...A MythTV system consists of backends, for recording and storing **[I]TV...' *

[I]but I can't get it to work!

[/I][/I] That is for another thread I guess.  Solve this little tinker first [Software Sources]

---

### Post by taurus on 2009-01-22
You can go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change to another server.  Try the Main Server to see if it works at all.

For more info about Medibuntu, check out this link, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

---

### Post by VerGuy on 2009-01-23
> **taurus said:**
> You can go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and change to another server.  Try the Main Server to see if it works at all.

For more info about Medibuntu, check out this link, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

Clicking on Repositories has no effect except for the mouse cursor changing to an animated circular object [System Busy?] The cursor then returns to normal without any other options being displayed. :(

---

### Post by Pumalite on 2009-01-23
Are you posting from the offending computer?

---

### Post by VerGuy on 2009-01-23
> **Pumalite said:**
> Are you posting from the offending computer?

I am at the moment [Not always the case]

---

### Post by Pumalite on 2009-01-23
You are sure you have a good connection in Ubuntu then.

---

### Post by VerGuy on 2009-01-23
> **Pumalite said:**
> You are sure you have a good connection in Ubuntu then.

Good connection to The Internet?

Yes. While it does occasionally go down it does not [usually] fail between my attempts to specify alternate software sources.

---

### Post by VerGuy on 2009-02-01
As the title says I have 'solved' this one.

Ubuntu started to find updates but not install them so I bit the bullet [copied off all of the items I wanted to keep and re-installed] Working perfectly now.

Thanks for all of the suggestions.

---

