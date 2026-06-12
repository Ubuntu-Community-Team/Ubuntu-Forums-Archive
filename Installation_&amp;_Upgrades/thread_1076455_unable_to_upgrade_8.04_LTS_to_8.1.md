---
title: "unable to upgrade 8.04 LTS to 8.1"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by wafflcommish on 2009-02-21
I have copied in my applicable information below.  Thanks in advance for your help.

root@server1:~# apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
root@server1:~# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'intrepid.tar.gz'
authenticate 'intrepid.tar.gz' against 'intrepid.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/main Sources
Done [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-updates/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) hardy-security/universe Sources
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/main Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/restricted Packages
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/universe Sources
Done downloading            
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/universe Sources
Done downloading            
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release.gpg
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates Release
Done [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security Release
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-updates/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/main Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/restricted Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/main Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/restricted Sources
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/universe Packages
Hit [http://mirror.anl.gov](http://mirror.anl.gov) intrepid-security/universe Sources
Done downloading            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://mirror.anl.gov/pub/ubuntu/dists/intrepid/Release](http://mirror.anl.gov/pub/ubuntu/dists/intrepid/Release) Unable to 
find expected entry mutliverse/binary-i386/Packages in Meta-index 
file (malformed Release file?) 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

---

### Post by konqueror7 on 2009-02-21
maybe the server is down...

my recommendation is do a clean install of 8.10...

---

