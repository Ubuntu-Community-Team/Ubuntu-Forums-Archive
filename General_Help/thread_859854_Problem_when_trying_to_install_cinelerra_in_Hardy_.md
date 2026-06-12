---
title: "Problem when trying to install cinelerra in Hardy Heron"
date: 2008-07-15
forum: General Help
---

### Post by s3a on 2008-07-15
deniz@deniz-desktop:~$ sudo wget [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list) -O /etc/apt/sources.list.d/akirad.list
[sudo] password for deniz: 
--00:03:13--  [http://repository.akirad.net/dists/hardy.list](http://repository.akirad.net/dists/hardy.list)
           => `/etc/apt/sources.list.d/akirad.list'
Resolving repository.akirad.net... 66.7.206.3
Connecting to repository.akirad.net|66.7.206.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 196 [text/plain]

100%[====================================>] 196           --.--K/s             

00:03:13 (12.42 MB/s) - `/etc/apt/sources.list.d/akirad.list' saved [196/196]

deniz@deniz-desktop:~$ wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
OK
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA                  
Get:1 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release.gpg [197B]              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA              
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg [189B]            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA      
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security Release.gpg [189B]           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security/main Translation-en_CA
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy Release.gpg             
Ign [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy/main Translation-en_CA
Ign [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release [58.5kB]              
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy Release                           
Get:5 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release [3024B]                 
Hit [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy/main Packages                 
Get:6 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy/main Packages [1807B]           
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
Get:8 [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy/main Sources [736B]    
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages [274kB]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources [79.7kB]        
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages [69.1kB]   
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources [15.9kB]    
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security/main Packages [29.6kB]      
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security/main Sources [7955B]        
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security/universe Packages [21.7kB]  
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-security/universe Sources [3308B]    
Fetched 625kB in 16s (37.1kB/s)                                                
Reading package lists... Done
deniz@deniz-desktop:~$ sudo apt-get install cinelerra-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  cinelerra-generic: Depends: liblame0 (>= 3.97) but it is not installable
                     Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
                     Depends: libquicktimehv-generic (= 1:2.1.0-1svn20080626akirad1) but it is not going to be installed
E: Broken packages
deniz@deniz-desktop:~$ 

**I followed this guide: [http://www.ubuntu-unleashed.com/2008/05/howto-install-cinerella-video-editor.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-cinerella-video-editor.html)**
Any help would be appreciated. Thanks!

---

