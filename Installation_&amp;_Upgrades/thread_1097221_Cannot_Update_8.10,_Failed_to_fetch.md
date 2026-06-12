---
title: "Cannot Update 8.10, Failed to fetch"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by newoldbie on 2009-03-15
After installing Open Office 3 months ago (I believe I used the following instructions: [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)) I have not been able to download any updates and Synaptic does not work.

When I click to update I get a message that says: Not all updates can be installed.... and I click to install a partial upgrade.

Then I get a window that says: Error authenticating some packages
and a lot of packages are listed.

Clicking close shuts down the update.

So lets go into Synaptic and see what happens.  Open the application and click RELOAD and get an error: Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

The following text is the scroll box of this dialog box:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  403 OK
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 OK
Some index files failed to download, they have been ignored, or old ones used instead.

After searching the forums for about 1 hour and trying a thing or two, no change.  Thinking someone will ask about etc/apt/soures.list I give it below:
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main universe
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

Would love to update my distribution.  Any thoughts.

---

### Post by SuperSonic4 on 2009-03-15
Uncomment the lines by removing the # at the start and run ```
sudo apt-get update
```
or copy and paste what I've posted below and then do the same command

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security main universe
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
```

---

### Post by newoldbie on 2009-03-29
Thank you for the kind support.  Did as you requested.
Here is the the terminal window dump:

bill@compaq:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg [189B]                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]          
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                     
Get:5 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg [189B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US         
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Get:6 [http://archive.canonical.com](http://archive.canonical.com) intrepid Release [7007B]                    
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [51.2kB]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Get:9 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages [2199B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release [44.0kB]        
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
  403 OK [IP: 66.211.136.146 8002]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
  403 OK [IP: 66.211.136.146 8002]
Get:11 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources [846B]            
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [97.3kB]     
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [25.7kB]          
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages [80.0kB]  
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [37.7kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages [14B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages [38.6kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages [14B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources [15.8kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources [14B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources [12.9kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources [14B]
Fetched 461kB in 4s (103kB/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 OK [IP: 66.211.136.146 8002]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  403 OK [IP: 66.211.136.146 8002]

E: Some index files failed to download, they have been ignored, or old ones used instead.
bill@compaq:~$ 
bill@compaq:~$ 

looks like I Have a bad public key?

---

### Post by newoldbie on 2009-03-29
I did the first try by deleting the # sign.  so I also tried copy and paste of the code you provided.  here is the result:

bill@compaq:/etc/apt$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
  403 OK
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
  403 OK
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
  403 OK
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
  403 OK
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages              
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
  403 OK
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
  403 OK
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
  403 OK
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
  403 OK
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz)  403 OK

E: Some index files failed to download, they have been ignored, or old ones used instead.
bill@compaq:/etc/apt$ 

A little bit different but still looks like it did not go through.

---

### Post by Ahmar on 2009-04-16
[I]Hi,
   I too am very new to Ubuntu--I've only had it on my computer for a month and a half--and I have the same problem.  I am tying to install desktop (The GUI worked fine and I'm not sure how I messed up the update, but I did), but I get the same message[/I]

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)

You may want to run apt-get update to correct those problems.


[I]However, once I run that command, I then get a message stating that:
[/I]

E: Could not open lock file /var/lib/apt/lists/lock - open(13 Permission denied)
E: Unable to lock the list directory

Any suggestions that you can offer will be greatly accepted...the only catch is that I really, really would prefer not to lose any of the data on my computer so a complete formatting and re-stall is preferably out-of-the-question.  Thank you in advance.

---

### Post by SuperSonic4 on 2009-04-16
> **newoldbie said:**
> I did the first try by deleting the # sign.  so I also tried copy and paste of the code you provided.  here is the result:

bill@compaq:/etc/apt$ sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
  403 OK
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release                    
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
  403 OK
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                           
  403 OK
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
  403 OK
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages              
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
  403 OK
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
  403 OK
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
  403 OK
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Packages
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Sources
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Sources
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Sources
  403 OK
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Sources
  403 OK
W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/intrepid/partner/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/intrepid/partner/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources.gz)  403 OK

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources.gz)  403 OK

E: Some index files failed to download, they have been ignored, or old ones used instead.
bill@compaq:/etc/apt$ 

A little bit different but still looks like it did not go through.

Is the internet as a whole ok? Sometimes it's a connection drop

> **Ahmar said:**
> [I]Hi,
   I too am very new to Ubuntu--I've only had it on my computer for a month and a half--and I have the same problem.  I am tying to install desktop (The GUI worked fine and I'm not sure how I messed up the update, but I did), but I get the same message[/I]

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_free_binary-i386_Packages)

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_intrepid_non-free_binary-i386_Packages)

You may want to run apt-get update to correct those problems.


[I]However, once I run that command, I then get a message stating that:
[/I]

E: Could not open lock file /var/lib/apt/lists/lock - open(13 Permission denied)
E: Unable to lock the list directory

Any suggestions that you can offer will be greatly accepted...the only catch is that I really, really would prefer not to lose any of the data on my computer so a complete formatting and re-stall is preferably out-of-the-question.  Thank you in advance.

Your error at the bottom is because you're trying to run a system task as root when you need to be user.

Duplicate entries does what it says on the tin, you can use ```
sudo nano /etc/apt/sources.list
``` or ```
gksu gedit /etc/apt/sources.list
``` depending on which text editor you prefer. When you open it you should be able to either delete a line or put a # sign infront of one of them although they seem to be different.


In both cases can you post the PPA of the source which has no public key? You can add them but at your own risk.

---

### Post by Ahmar on 2009-04-17
> **SuperSonic4 said:**
> 


Your error at the bottom is because you're trying to run a system task as root when you need to be user.

Duplicate entries does what it says on the tin, you can use ```
sudo nano /etc/apt/sources.list
``` or ```
gksu gedit /etc/apt/sources.list
``` depending on which text editor you prefer. When you open it you should be able to either delete a line or put a # sign infront of one of them although they seem to be different.


In both cases can you post the PPA of the source which has no public key? You can add them but at your own risk.

Thank you for your help!  I made progress; at least, I think so. I was able to fix the duplicate entries via the method that you suggested, but I still received the following message.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

And, unfortunately, I don't understand what you mean regarding the ppa so I am unable to provide any additional information on that front.

---

### Post by newoldbie on 2009-05-12
Giving up since no-one seems to know what to do next.  Will let the system run, mostly used by kids for surfing and homework.  At some point will re-install from ground up, maybe next major release?

---

### Post by zvacet on 2009-05-13
You can use this source list 

> #deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

and you can add your ppa repo.

```
sudo apt-get update && sudo apt-get upgrade
```

You will probably get error message for ppa repo and then type in terminal

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -
```

Replace **KEY** with 9423A34CCA967634

---

