---
title: "apt-get repeatedly downloads the same packages"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by dougalmcshlong on 2009-09-17
Had this problem with 8.04 LTS Server then reinstalled - same problem...

I enable all sources in sources.list then run apt-get update (+reboot) then apt-get upgrade (+reboot). Now everytime I run apt-get update it downloads th same set of files - it is never satisfied! What is going on?

This is the set of files it downloads EVERYTIME I run it...

root@server:~# apt-get update
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg [189B]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU                                                                     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU                                                                                         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU                                                                                           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU                                                                                         
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg [189B]                                                                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU                                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU                            
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_AU                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_AU             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU                            
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports Release.gpg [189B]                                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/main Translation-en_AU                                
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_AU                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/restricted Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/universe Translation-en_AU                            
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/multiverse Translation-en_AU                          
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release [65.9kB]                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages              
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports Release [51.2kB]                             
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages [1173kB]                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages [6397B]
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources [338kB]
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources [1488B]
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages [4254kB]
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources [1323kB]                                                                                         
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages [174kB]                                                                                       
Get:14 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources [60.9kB]                                                                                       
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages [463kB]                                                                                     
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages [7763B]                                                                               
Get:17 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources [117kB]                                                                                      
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources [941B]                                                                                 
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages [200kB]                                                                                 
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources [43.4kB]                                                                                 
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages [28.7kB]                                                                              
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources [5394B]                                                                                
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/main Packages [112kB]                                                                                   
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/restricted Packages [14B]                                                                               
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/universe Packages [112kB]                                                                               
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/multiverse Packages [14.7kB]                                                                            
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/main Sources [16.3kB]                                                                                   
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/restricted Sources [14B]                                                                                
Get:29 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/universe Sources [26.4kB]                                                                               
Get:30 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-backports/multiverse Sources [4064B]                                                                              
Fetched 8658kB in 13s (626kB/s)                                                                                                                             
Reading package lists... Done


It's giving me no confidence to continue with the install.

I am a bit of a noob - am I missing something stupid?:confused:

---

### Post by VMC on 2009-09-17
No. What it is getting is the information from ubuntu repositories that you have at your "/etc/apt/sources.list". You can cat out that file and compare it to what its getting.

Is there any packages that come after that. Does it ask you if you want to install or not?

---

### Post by dougalmcshlong on 2009-09-17
Sounds a bit weird - dowloading 8meg just to say there are no updates.
 
I'm sure when I've run it through the GUI it has in the past said something like - your system is up to date. If I run it through the GUI at the moment it is doing exactly the same as from the command line...
 
The sources.list is the default one with all repositories unhashed.

---

