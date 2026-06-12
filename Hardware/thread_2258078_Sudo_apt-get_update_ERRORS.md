---
title: "Sudo apt-get update ERRORS"
date: 2014-12-24
forum: Hardware
---

### Post by Deathstalker96 on 2014-12-24
Hello , Linux user. I'm new to Linux and running Ubuntu 14.10 . 
well I was running terminal last night I ran "Sudo apt-get update " and ran into some errors . like I said im new to any linux based os . I'm not sure if this error needs attention or if it's just a minor setback if anything. I would like to know how to fix this tho it bugs me to see errors on my computer. any help will be appreciated as I am very new to linux. and a detailed step by step fix would be very appreciated .

This is what i get when i run "Sudo apt-get update"   

```
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic InRelease                                 
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) utopic InRelease [5,631 B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates InRelease                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic InRelease                                  
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease                               
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic InRelease                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security InRelease                        
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [549 B]               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release.gpg                       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/contrib amd64 Packages/DiffIndex     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports Release.gpg                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security Release.gpg                      
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/non-free amd64 Packages/DiffIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates Release                           
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/contrib i386 Packages/DiffIndex      
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [604 B]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security Release                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/non-free i386 Packages/DiffIndex     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Sources                               
Get:4 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [804 B]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main i386 Packages                         
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main amd64 Packages                     
Get:5 [http://download.virtualbox.org](http://download.virtualbox.org) utopic/contrib amd64 Packages [1,004 B]   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages                      
Get:6 [http://download.virtualbox.org](http://download.virtualbox.org) utopic/non-free amd64 Packages [14 B]     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Get:7 [http://download.virtualbox.org](http://download.virtualbox.org) utopic/contrib i386 Packages [1,006 B]    
Get:8 [http://download.virtualbox.org](http://download.virtualbox.org) utopic/non-free i386 Packages [14 B]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic Release                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en_CA                     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en_CA                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Sources              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Sources              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted amd64 Packages       
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/contrib Translation-en_CA            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse amd64 Packages
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/contrib Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted i386 Packages        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/non-free Translation-en_CA           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse i386 Packages        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) utopic/non-free Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/restricted Translation-en
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_CA               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Sources       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main amd64 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe amd64 Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse amd64 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main i386 Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en_CA       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/multiverse Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/restricted Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-en_CA   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic/universe Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main amd64 Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe amd64 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main amd64 Packages            
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/main Translation-en 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main i386 Packages             
  404  Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en_CA         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main i386 Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) utopic/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) utopic-security/universe Translation-en
Fetched 9,626 B in 6s (1,600 B/s)                                              
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) utopic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Yellow Pasque on 2014-12-24
The error will not stop you from using apt. Quite simply, you have a couple outdated sources from precise and also this outdated PPA: [https://launchpad.net/~glasen/+archive/ubuntu/intel-driver](https://launchpad.net/~glasen/+archive/ubuntu/intel-driver)
You need to remove them from your sources (look in /etc/apt/sources.list.d)

---

### Post by Deathstalker96 on 2014-12-24
Ya I just followed your directions and i could easly find the old packages then deleted them . preee easy fix. Thank you for your help tho!!

---

