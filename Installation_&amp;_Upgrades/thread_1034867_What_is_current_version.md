---
title: "What is current version?"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by BkkBonanza on 2009-01-09
Hello,
I installed Ubuntu from the 8.04 Install CD.
It has been updating all along since then.
Recently it said it was doing an upgrade to 8.10
At first it had issues but eventually it seemed to catch up and complete.
When I type "uname -r" I get kernel 2.6.24-22 generic
But someone just told me that the 8.10 kernel is supposed to be 2.6.27
So what's wrong? How do I get my system up to date properly? Or is it already?
I'm asking because apparently my Acer notebook will start using acer-wmi instead of acer-acpi and should work a bit better.
Thanks for input on this.
Chris :)

---

### Post by blazemore on 2009-01-09
Run another update, it will be using the new repositories this time:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BkkBonanza on 2009-01-09
Must be something wrong with my repository settings. I ran the command as you suggested and it hit a whole bunch of "hardy" repositories but in the end found nothing to update or upgrade. Do I need to change some repo config?
Here's the result I got:

Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Get:1 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main Packages                                                                           
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/restricted Packages                                                                     
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main Sources                                                                            
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/restricted Sources                                                                      
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/universe Packages                                                                       
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/universe Sources                                                                        
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse Packages                                                                     
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse Sources                                                                      
Get:3 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/main Sources [105kB]                                                          
Get:4 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/restricted Sources [903B]                                                     
Get:5 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/universe Packages [155kB]                                                     
Get:6 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/universe Sources [34.7kB]                                                     
Get:7 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/multiverse Packages [26.4kB]                                                  
Get:8 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/multiverse Sources [4601B]                                                    
Fetched 385kB in 16s (24.0kB/s)                                                                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by BkkBonanza on 2009-01-09
Oh. I just saw in another post that the upgrade to 8.10 is not automatic. You have to manually invoke that. So I guess I haven't done it as thought then. Looks like all I have is an up-to-date 8.04 if I understand this now. I have to manually tell it to upgrade as per details here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

