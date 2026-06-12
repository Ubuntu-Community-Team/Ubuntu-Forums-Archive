---
title: "Ubuntu 9.04 -&gt; 9.10 upgrade fails &quot;Starting Administrative.....&quot;"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Dubbayoo on 2009-11-04
I've applied all 9.04 updates

[LIST]
[*]I select Upgrade within Update Manager
[*]Select upgrade on release notes page
[*]2 files are downloaded
[*]The "Starting Administrative..." window opens then closes within 1-2 seconds and thats it.
[/LIST]

I have tried 9-10 times thru various reboots. The system has run near flawlessly for months if not years. What should I try next?

---

### Post by jjcv on 2009-11-04
Have you tried it from a terminal:

gksudo "update-manager -c"

Alternatively if the core files in /etc/apt have been updated to karmic you can do:

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Dubbayoo on 2009-11-04
Yes, I have.

> steve@makuri:~$ **sudo apt-get update**
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2540B]                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [665B]                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Fetched 3394B in 1s (2070B/s)
Reading package lists... Done
steve@makuri:~$ **sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

