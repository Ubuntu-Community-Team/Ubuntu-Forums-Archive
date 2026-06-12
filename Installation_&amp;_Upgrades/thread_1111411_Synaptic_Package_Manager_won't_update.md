---
title: "Synaptic Package Manager won't update"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by darthabne on 2009-03-30
Hi all,I've just started using Ubuntu for a few weeks now and have been really enjoying it. This weekend got a bigger HD for my laptop and installed 8.10, but I now have a problem.

I've tried updating the Manager to get third party(multiverse) software to come up, but it won't seem to update. I tried updating it through Terminal and this is what I got 

darthbane@darthbane-laptop:~$ sudo apt-get update
[sudo] password for darthbane: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
Reading package lists... Done
darthbane@darthbane-laptop:~$ 

When I search for programs like VLC, it shows no results. Anyone know how to fix this?

Any help is appreciated.

---

### Post by lindsay7 on 2009-03-30
Take a look at these sites.

[http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/](http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/)


[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)



[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html)

---

### Post by darthabne on 2009-03-30
I got VLC, but still having trouble updating the repositories

Here's what I got from following the first link:

For "sudo apt-get update"

darthbane@darthbane-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release [51.2kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages [320kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages [8097B]   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages [82.9kB]    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages [10.9kB]  
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources [101kB]          
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources [2474B]    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources [19.4kB]     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources [4118B]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages              
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages [6710B] 
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources [28.0kB]       
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources [1154B]  
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources [6676B]    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources [1860B]  
Fetched 645kB in 11s (54.3kB/s)                                                
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
darthbane@darthbane-laptop:~$ 


For "sudo apt-get upgrade"

darthbane@darthbane-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darthbane@darthbane-laptop:~$ 

Thanks lindsay7 for the links.

---

### Post by lindsay7 on 2009-03-30
See if you got everything you needed from these two sites too.


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by darthabne on 2009-03-31
Ah! There we go. I got the repositories updated.

Thanks again lindsay7 for al your help.

---

