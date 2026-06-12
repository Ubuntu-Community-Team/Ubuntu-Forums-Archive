---
title: "Logitech Roller-ball Mouse fails after I log-in"
date: 2016-03-12
forum: Hardware
---

### Post by RayArdia on 2016-03-12
I have used the same roler-ball mouse for years, I prefer it to any other kind of  mouse or touchpad especially when using Gimp or QCAD as it gives much more precise control.
I have lately found that the mouse will suddenly stop responding for no apparent reason and the only way to 'get it back' is to reboot. Lately this too has become problematic as Ubuntu freezes at the Ubuntu 'row of dots' screen - the dots follow their L_R sequence but nothing else happens.
I have tried sudo apt-get update - terminal output is as follows:-

ray@ray-Aspire-5735:~$ sudo apt-get update
[sudo] password for ray: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]          
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty InRelease                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:3 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [106 kB]         
Get:5 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports InRelease [65.9 kB]        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [34.0 kB]    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty Release.gpg                            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B]  
Get:9 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/main Sources [262 kB]        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [404 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:12 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [125 kB]
Get:14 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/universe Sources [151 kB]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Get:16 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/multiverse Sources [5,946 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Get:17 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/main i386 Packages [692 kB]
Get:18 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:19 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/universe i386 Packages [340 kB]
Get:20 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-updates/universe Translation-en        
Get:21 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/main Sources [8,661 B]    
Get:22 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Get:23 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/universe Sources [34.0 kB]
Get:24 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:25 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/main i386 Packages [9,814 B]
Get:26 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:27 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/universe i386 Packages [41.0 kB]
Get:28 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty Release                                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/main Sources                           
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/universe i386 Packages       t          
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/restricted Translation-en_nd ouGB           
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/universe Translation-en_GB             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 2,475 kB in 19s (130 kB/s)                                             
Reading package lists... Done
ray@ray-Aspire-5735:~$ 

How can I find out what is causing these problems, and of course fix it?

---

