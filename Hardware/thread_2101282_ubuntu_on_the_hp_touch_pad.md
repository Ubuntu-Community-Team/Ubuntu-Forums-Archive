---
title: "ubuntu on the hp touch pad"
date: 2013-01-04
forum: Hardware
---

### Post by yesfull man on 2013-01-04
ok so i'm currently trying to install ubuntu on my hp touch pad.

now im following the instructions but i keep running into problems while preping ubunu on my pc. 

the bigest problem is when i enter in 
<sudo apt-get install git>

it says it cant find the file. now since the tutorials are all saying use 11.04, ive been using that. will this still work if i do a recent one like 12.04

if you need the link to the tutorial im using i can send it.

my other qustion is should i just not worry about this and shoot for ubuntu mobile?

---

### Post by ojdon on 2013-01-04
git should be in the repo. Have you updated the repository lately?

> sudo apt-get update

If not it's definitely in 12.04 and later.

---

### Post by yesfull man on 2013-01-04
i just installed 11.04. and i got this.


Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Cou

---

### Post by yesfull man on 2013-01-05
ok so i tried it on both 12.04 and 11.04. and i ended up bricking it twice. luckly webos doctor helped fix it. that being said idk what went wrong. if anybody has goten it to work and is willing to help and or direct me to the tutorial they used that would be awsome!

---

