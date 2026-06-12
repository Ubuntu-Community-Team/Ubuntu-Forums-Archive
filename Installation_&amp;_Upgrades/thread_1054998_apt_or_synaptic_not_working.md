---
title: "apt or synaptic not working"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by kdub on 2009-01-30
My apt get? synaptic? add-remove? doesn't seem to work. I requested help when two upgrades ago the synaptic froze and was told to use a sudo apt get then sudo apt upgrade (it was either that or synaptic , synaptic upgrade-it's at work and I'm home) that cleared the problem temp. but now it happens every time I try to upgrade or download and install. the ubuntu download box pops up and every thing freezes. Any ideas?
thanx
ken

---

### Post by avtolle on 2009-01-30
Flying a bit blind here, given the lack of information, but try```
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by taurus on 2009-01-30
If there is an error when you run **sudo apt-get update** from a terminal, at least post the whole error message so others can diagnose your problem.  Otherwise, how would anyone know what's wrong with your system?

---

### Post by ypeskov on 2009-01-30
Just not to start a new topic, I have next error messages when trying to do something with apt:

apt-get update && sudo apt-get upgrade:
...
...
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when I am trying to do that I get next error:
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

what can I do?

---

### Post by kdub on 2009-01-30
Well- 
I did the sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade comand and I got a bunch of lines telling me that my kernal, drivers, and a bunch of other stuff were being updated. I'm now back from work and the "alert new upgrade arrow" was showing.I clicked on the arrow,clicked download,entered my sudo password and waited for the download to start-and waited, and waited, still waitng, and waiting....froze just like before in the origanal post that was so poorly expressed-sorry.Any other ideas?
thanx,
ken

---

### Post by avtolle on 2009-01-30
From the terminal please do```
sudo aptitude update && sudo aptitude safe-upgrade
```and post any error messages. TIA.

---

### Post by Pumalite on 2009-01-30
Try:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by kdub on 2009-01-30
Avtolle,
I got this
dub@kbw:~$ sudo aptitude update
[sudo] password for kdub: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US                
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?      and this
kdub@kbw:~$ sudo aptitude safe-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Is it normal?

Pumalite-I got this from sudo apt-get update

kdub@kbw:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
And also this
kdub@kbw:~$ sudo apt-get dist-upgrade
[sudo] password for kdub: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kdub@kbw:~$ 
Again is this normal?
thanx,
kdub (ken)

---

### Post by avtolle on 2009-01-30
Is the upgrade manager still open? If it is, close it. That's the reason for the Error you received about the lock. Then try either my commands or Pumalite's again.

---

### Post by kdub on 2009-01-30
> **avtolle said:**
> Is the upgrade manager still open? If it is, close it. That's the reason for the Error you received about the lock. Then try either my commands or Pumalite's again.

How do I turn off upgrade manager? I just rebooted and the download/upgrade arrow is back-kind of afraid to touch it before I get the OK.
thanks,
ken

---

### Post by avtolle on 2009-01-30
If the arrow is back, don't click on it! Open a terminal and use the commands that either Pumalite or I gave you above (your choice). Then, let us know about any error messages, etc.

---

