---
title: "I can't download the repository directories for update"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by xxrafaelxx3 on 2009-01-26
I just got a Dell laptop with Hardy installed, and I'm trying to update to Intrepid.  However, when I start the update manager, it errors and says the following:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.


I've tried changing to numerous different download servers and it still does this.  Is this a server problem or is it a problem with my software?

Thanks for your help!

---

### Post by Partyboi2 on 2009-01-26
There is no binary-lpia packages in those  repos. What model dell have you got?

---

### Post by xxrafaelxx3 on 2009-01-26
i have a mini 12.

---

### Post by Partyboi2 on 2009-01-26
You will probably need to change your sources.list and add these ones
```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
```
If you are not sure how to add them and to disable the other ones, then open a terminal (Applications>Accessories>Terminal) and post your sources.list by typing
```
cat /etc/apt/sources.list
``` and I will give you a hand.

---

### Post by xxrafaelxx3 on 2009-01-26
is this the way its supposed to look? (attachment)

---

### Post by Partyboi2 on 2009-01-27
Looks like it.

---

### Post by jzinna on 2009-01-27
I have the same problem.  I had Ubuntu installed previously and was running ok, but I deleted everything on my machine and started all over, installed Ubuntu from the same disk I had, and started with that problem.  I don't have Dell, it's a clone, so I think I can't use the links you just posted, right?

My sources list follows:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb [http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/](http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/](http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/](http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/) hardy-security main restricted multiverse
deb-src [http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/](http://carroll.cac.psu.edu/pub/linux/distributions/ubuntu/) hardy-security main restricted multiverse #Added by software-properties
deb-src [http://espelhos.edugraf.ufsc.br/ubuntu/](http://espelhos.edugraf.ufsc.br/ubuntu/) hardy main restricted #Added by software-properties




deb [http://espelhos.edugraf.ufsc.br/ubuntu/](http://espelhos.edugraf.ufsc.br/ubuntu/) hardy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted





Thanks!!!

---

### Post by Partyboi2 on 2009-01-27
> **jzinna said:**
> I have the same problem.  I had Ubuntu installed previously and was running ok, but I deleted everything on my machine and started all over, installed Ubuntu from the same disk I had, and started with that problem.  I don't have Dell, it's a clone, so I think I can't use the links you just posted, right?
Thanks!!!

Those repos I posted are for the dell mini. You are probably getting a different error message then the op, looking at your sources.list you probably need to disable the cdrom repo.
Open a terminal and open your sources.list
```
gksu gedit /etc/apt/sources.list
``` stick a # infront of 
```
deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```so becomes
```
# deb cdrom:[Ubuntu 8.04.2 _Hardy Heron_ - Release i386 (20090121.2)]/ hardy main restricted
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```then save, and back in the terminal type
```
sudo apt-get update
``` and post the results.

---

### Post by mercedes on 2009-01-27
I am having a similar problem with my Dell Mini. It almost appears as though I have redundant sources listed. Is that possible? 

This is my source list:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

---

### Post by jzinna on 2009-01-27
From the terminal I got this after removing the Cd repos:

Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates Release.gpg
Get:1 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy Release.gpg [189B]
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/universe Translation-en_US                                      
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/main Translation-en_US            
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US        
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/multiverse Translation-en_US      
Get:2 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates Release.gpg [189B]      
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/universe Translation-en_US                              
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/main Translation-en_US                          
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/multiverse Translation-en_US                    
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/restricted Translation-en_US                    
Get:3 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-security Release.gpg [189B]                           
Ign [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-security/universe Translation-en_US                     
Get:4 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy Release [65.9kB]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/main Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/restricted Translation-en_US
Get:5 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates Release [58.5kB]               
Get:6 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-security Release [58.5kB]                                   
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/multiverse Translation-en_US  
Get:7 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/main Sources [338kB]                                   
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/universe Translation-en_US                                
Get:8 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/restricted Sources [1488B]           
Get:9 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/universe Packages [4293kB]
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security Release.gpg                
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/main Translation-en_US                                        
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/restricted Translation-en_US          
Ign [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/multiverse Translation-en_US          
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates Release                                 
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security Release                                                     
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/main Packages                                                
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/restricted Packages                      
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/multiverse Packages                      
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/restricted Sources                                                             
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/main Sources                                                                   
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/multiverse Sources                                                             
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/universe Sources                                                               
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-updates/universe Packages                                                              
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/main Packages                                                                 
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/restricted Packages                                                           
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/multiverse Packages                                                           
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/main Sources                                                                  
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/restricted Sources                                                            
Hit [http://carroll.cac.psu.edu](http://carroll.cac.psu.edu) hardy-security/multiverse Sources                                                            
Get:10 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/main Packages [1178kB]                                                         
Get:11 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/restricted Packages [6986B]                                                    
Get:12 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/multiverse Packages [179kB]                                                    
Get:13 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/universe Sources [1323kB]                                                      
Get:14 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy/multiverse Sources [60.9kB]                                                    
Get:15 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/universe Packages [158kB]                                              
Get:16 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/main Packages [410kB]                                                  
Get:17 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/multiverse Packages [26.4kB]                                           
Get:18 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-updates/restricted Packages [8001B]                                            
Get:19 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-security/universe Packages [53.7kB]                                            
Get:20 [http://espelhos.edugraf.ufsc.br](http://espelhos.edugraf.ufsc.br) hardy-security/universe Sources [8722B]                                              
Fetched 8229kB in 46s (178kB/s)                                                                                             
Reading package lists... Done


I don't know what the "Hit" means, but at least it hasn't "Failed" like before...


And updating from the Update Manager gets me some "failed" errors while downloading, but then the "Errors" box that used to appear doesn't pop up....

I presume it's fixed, no updates have appeared but I have the 8.04 version just downloaded from the site (The Alternate CD).... so it just may be I don't need any.
Anyway, if updates don't appear for some time, I'll come again....

Thanks everybody!!!

---

### Post by mercedes on 2009-01-27
I think I found the answer to my Dell Mini problem here:
[http://mydellmini.com/forum/dell-repository-update-failure--p6816.html](http://mydellmini.com/forum/dell-repository-update-failure--p6816.html)

In Software Sources, I unchecked all of the Ubuntu sources, so I am only downloading from third-party (dell) sources. I think.

---

