---
title: "Update Manager stopped working?"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by nathan726 on 2009-09-27
I've started having problems with update manager and when I try to update:

```
sudo apt-get update
Get:1 http://au.archive.ubuntu.com jaunty Release.gpg [189B]
Hit http://au.archive.ubuntu.com jaunty/main Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty/restricted Translation-en_AU           
Ign http://au.archive.ubuntu.com jaunty/universe Translation-en_AU             
Ign http://au.archive.ubuntu.com jaunty/multiverse Translation-en_AU           
Get:2 http://au.archive.ubuntu.com jaunty-updates Release.gpg [189B]           
Ign http://au.archive.ubuntu.com jaunty-updates/main Translation-en_AU         
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Translation-en_AU   
Ign http://au.archive.ubuntu.com jaunty-updates/universe Translation-en_AU     
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Translation-en_AU   
Get:3 http://au.archive.ubuntu.com jaunty-security Release.gpg [189B]          
Ign http://au.archive.ubuntu.com jaunty-security/main Translation-en_AU        
Ign http://au.archive.ubuntu.com jaunty-security/restricted Translation-en_AU  
Ign http://au.archive.ubuntu.com jaunty-security/universe Translation-en_AU    
Ign http://au.archive.ubuntu.com jaunty-security/multiverse Translation-en_AU  
Hit http://au.archive.ubuntu.com jaunty Release                                
Hit http://au.archive.ubuntu.com jaunty-updates Release                        
Hit http://au.archive.ubuntu.com jaunty-security Release                       
Hit http://au.archive.ubuntu.com jaunty/main Packages                          
Hit http://au.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://au.archive.ubuntu.com jaunty/main Sources       
Hit http://au.archive.ubuntu.com jaunty/restricted Sources 
Hit http://au.archive.ubuntu.com jaunty/universe Packages  
Hit http://au.archive.ubuntu.com jaunty/universe Sources   
Hit http://au.archive.ubuntu.com jaunty/multiverse Packages
Hit http://au.archive.ubuntu.com jaunty/multiverse Sources 
Hit http://au.archive.ubuntu.com jaunty-updates/main Packages
Hit http://au.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://au.archive.ubuntu.com jaunty-updates/main Sources
Hit http://au.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://au.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://au.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://au.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://au.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://au.archive.ubuntu.com jaunty-security/main Packages
Hit http://au.archive.ubuntu.com jaunty-security/restricted Packages
Hit http://au.archive.ubuntu.com jaunty-security/main Sources
Hit http://au.archive.ubuntu.com jaunty-security/restricted Sources
Hit http://au.archive.ubuntu.com jaunty-security/universe Packages
Hit http://au.archive.ubuntu.com jaunty-security/universe Sources
Hit http://au.archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://au.archive.ubuntu.com jaunty-security/multiverse Sources
Fetched 567B in 47s (12B/s)
Reading package lists... Done

```
Any ideas?  Thanks.

---

### Post by Partyboi2 on 2009-09-27
Hi. looking at all those outputs there does not appear to be any thing wrong.
If you are referring to the 'ign' parts of the 'sudo apt-get update' that is normal, it just means that you already have the latest of that file and that it does not need to be downloaded again.

---

### Post by nathan726 on 2009-09-27
It updates way too fast - I mean after two seconds it is finished updating and I have no new updates to install. Usually it takes about 5 minutes and have a dozen new updates to install.

I haven't had any new updates for about a month. Isn't that a little odd?

---

### Post by Partyboi2 on 2009-09-28
I normally find the Australian server slow, so I generally use the main server. I am not currently using Jaunty so not sure when the last lot of updates were, but I would think you should have had a couple within the last  month.

---

### Post by nathan726 on 2009-09-29
I was too quick to assume the worst - I got a bunch of updates today via the AU server!

---

