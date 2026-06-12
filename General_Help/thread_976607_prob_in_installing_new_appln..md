---
title: "prob in installing new appln."
date: 2008-11-09
forum: General Help
---

### Post by arunprasad13 on 2008-11-09
hi..i m not able to install anything from the synaptic packet manager..it doesnot connect to the internet..

whn i use "apt-get install" command it throws a 404 server not found error

"apt-get update" also trows a similar error ...


what am i to do?:(

---

### Post by teddks on 2008-11-09
What are the contents of your /etc/apt/sources.list?

My thought is that you're using a faulty mirror or have some other configuration issue present in that file. I assume you are connected to the internet and can browse websites and whatnot?

---

### Post by arunprasad13 on 2008-11-10
yes i m connected to the internet and able to browse the net...this is the error i get when i try to install vlc

arun@arun-desktop:~$ sudo apt-get install vlc
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xext-dev libdevhelp-1-0 x11proto-kb-dev libgbf-1-0 libapr0
  anjuta-common libxdmcp-dev libpng12-dev libsvn0 xtrans-dev x11proto-core-dev
  devhelp-common libxext-dev libjpeg62-dev zlib1g-dev libgbf-1-common
  x11proto-input-dev libfreetype6-dev libgdk-pixbuf2 libxau-dev liborbit0
  libx11-dev x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libvlc0 vlc-nox
Suggested packages:
  mozilla-plugin-vlc
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  libvlc0 vlc vlc-nox
0 upgraded, 3 newly installed, 0 to remove and 204 not upgraded.
Need to get 6787kB of archives.
After unpacking 18.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libvlc0 vlc-nox vlc
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe libvlc0 0.8.6.release-0ubuntu1~edgy1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe vlc-nox 0.8.6.release-0ubuntu1~edgy1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe vlc 0.8.6.release-0ubuntu1~edgy1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
arun@arun-desktop:~$

---

### Post by teddks on 2008-11-10
> **arunprasad13 said:**
> yes i m connected to the internet and able to browse the net...this is the error i get when i try to install vlc

arun@arun-desktop:~$ sudo apt-get install vlc
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xext-dev libdevhelp-1-0 x11proto-kb-dev libgbf-1-0 libapr0
  anjuta-common libxdmcp-dev libpng12-dev libsvn0 xtrans-dev x11proto-core-dev
  devhelp-common libxext-dev libjpeg62-dev zlib1g-dev libgbf-1-common
  x11proto-input-dev libfreetype6-dev libgdk-pixbuf2 libxau-dev liborbit0
  libx11-dev x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libvlc0 vlc-nox
Suggested packages:
  mozilla-plugin-vlc
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  libvlc0 vlc vlc-nox
0 upgraded, 3 newly installed, 0 to remove and 204 not upgraded.
Need to get 6787kB of archives.
After unpacking 18.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libvlc0 vlc-nox vlc
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe libvlc0 0.8.6.release-0ubuntu1~edgy1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe vlc-nox 0.8.6.release-0ubuntu1~edgy1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe vlc 0.8.6.release-0ubuntu1~edgy1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/libvlc0_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu1~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu1~edgy1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
arun@arun-desktop:~$

Those files do indeed not exist on that server.

Have you tried updating your local package cache (sudo apt-get update)? 

Two things would be helpful: the output of 'lsb_release -a' and 'cat /etc/apt/sources.list'.

---

### Post by Zill on 2008-11-10
Looks to me like you are trying to update Edgy.

This reached End-of-Life in April 2008 so is no longer supported.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by arunprasad13 on 2008-11-11
i some how managed to guess that the version of my ubuntu is outdated..i have been trying to update my sources.list

but i get the following error when use the "apt-get update"


sudo apt-get update
Password:
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                                                                                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                                                                                                   
Err [http://dl.google.com](http://dl.google.com) stable Release                                                                                       
  
Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [189B]                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US                                                         
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                                                             
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                                                                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US                                     
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release [5995B]                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                      
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                           
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                       
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                                                                                               
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                                                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                                                                                             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                                                                                            
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                                                                                                      
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                                                                                                      
  404 Not Found [IP: 91.189.88.40 80]
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                                                                                                          
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                                                                                                        
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                                                                                             
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                                                                                                       
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                                                                                                       
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                                                                                                         
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                                                                                                    
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                                                                                              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                                                                                              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                                                                                                
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                                                                                                     
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                                                                                               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                                                                                               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources                                                                                                 
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                                                                                                  
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                                                                            
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                                                                              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                                                                                            
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                                                                                                   
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                                                                                             
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                                                                                               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                                                                                             
  404 Not Found [IP: 91.189.88.40 80]
Fetched 7673B in 10s (751B/s)                                                                                                                               
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


and the other outputs u asked for are here

arun@arun-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy


arun@arun-desktop:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by arunprasad13 on 2008-11-11
hi..i will paste the out put which u asked for

arun@arun-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy

.what should i do to install a new appln if i have attained end of life.

---

### Post by arunprasad13 on 2008-11-11
arun@arun-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.10
Release:        6.10
Codename:       edgy
arun@arun-desktop:~$ vi /etc/apt/sources.list


arun@arun-desktop:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END


THIS WHAT HAPPEN WHEN I TRY TO UPDATE THE SOURSES.LIST

arun@arun-desktop:~$ sudo apt-get update
Password:
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                                                                                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg                                                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                                                                                                   
Err [http://dl.google.com](http://dl.google.com) stable Release                                                                                       
  
Get:2 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [189B]                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US                                                         
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                                                                               
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US                                                             
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                                                                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US                                     
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release [5995B]                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                       
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                      
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                           
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                       
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                                                                                               
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                                                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                                                                                             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                                                                                                            
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                                                                                                      
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                                                                                                      
  404 Not Found [IP: 91.189.88.40 80]
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                                                                                                          
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                                                                                                        
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                                                                                                             
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources                                                                                                       
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources                                                                                                       
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                                                                                                         
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                                                                                                    
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                                                                                              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                                                                                              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                                                                                                
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                                                                                                     
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                                                                                               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                                                                                               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources                                                                                                 
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                                                                                                  
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages                                                                                            
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                                                                                              
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages                                                                                            
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages                                                                                                   
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                                                                                             
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                                                                                               
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                                                                                             
  404 Not Found [IP: 91.189.88.40 80]
Fetched 7673B in 10s (751B/s)                                                                                                                               
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.40 80]
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
arun@arun-desktop:~$ 
arun@arun-desktop:~$

---

### Post by arunprasad13 on 2008-11-11
if i have attained end of life what should i do to update my ubuntu..without losing any of my data..any service pack kind of option is available ..pl guide me through this.i m a new to this..:confused:

---

### Post by Zill on 2008-11-11
You will see from the [Releases]("https://wiki.ubuntu.com/Releases") info that Ubuntu standard releases are supported for 18 months, while Ubuntu LTS (Long Term Support) releases are supported for 3 years.

If you install every release it is relatively simple to upgrade each time from the old to the new release.  However, it is not so easy to do if one or more releases are missed, as the missing ones must first be installed sequentially.  In your case, there are three releases "missing" between Edgy and the current release, Intrepid.  So, I suggest upgrading sequentially is not really appropriate in this case.

You therefore now have a choice of installing either Hardy (the Long Term Support release), or Intrepid.  Just consider how long you want to keep the system before upgrading before deciding which release to install.

Then, download and burn the appropriate ISO CD from [this link]("http://www.ubuntulinux.org/getubuntu/download").

Backup all the data you want to retain to a different media then insert your new ISO CD and start the installer.  If you want to preserve your existing data it helps if your /home directory is on a different partition.  If so then just reformat your / (root) partition and ensure that /home is *not* reformatted during the install.  This should leave your data intact but you should always have a backup just in case. ;-)

If your /home directory is not on a different partition, now is a good time to do this when you reformat the HDD!  You will lose your data in this case when you reformat but just restore it from the backups you made earlier after the software installation has finished.

Hope this makes sense (and that there are no stupid errors!) but if not then just ask.  Good luck.

---

### Post by teddks on 2008-11-11
You can also just upgrade to 7.04, and then upgrade to 7.10, which will meet it's End Of Life in April of 2009. You could go all the way and upgrade to 8.04 and even 8.10.

To upgrade, just launch update-manager with the dist-upgrade flag:

```
gksu update-mananager -d
```

...and hit the "Upgrade" button that'll be at the top of the screen.


You'll go through a process that will install 7.04 on your computer, and then you can go through the same process again to install 7.10, which you can either use until April or upgrade again.

---

### Post by spibou on 2008-11-11
arunprasad13, I've had the [ same problem](http://ubuntuforums.org/showthread.php?t=923677&highlight=no+more+edgy%3F). I decided to stick with edgy and compile from source any additional stuff I need. It's a bummer but the lesser evil for me. Compiling from source has its advantages too since on a number of occasions I've found important components missing from the Ubuntu packages like for example documentation in the development version of a library.

---

### Post by arunprasad13 on 2008-11-12
i completely understood what zill and teddks explained to me..but i dont quite understand what compiling from source means..

for example : i wanted to install vlc to play DVDs , now that i m not able to do it either from synaptic or from apt-get..how can i do this by compiling the source.

---

### Post by teddks on 2008-11-12
> **arunprasad13 said:**
> i completely understood what zill and teddks explained to me..but i dont quite understand what compiling from source means..

for example : i wanted to install vlc to play DVDs , now that i m not able to do it either from synaptic or from apt-get..how can i do this by compiling the source.

You would have to hunt down the package and libraries you need, download them, then use terminal to manually build and install them.

It's a lot simpler to just upgrade twice than to do that for everything, because you're essentially replacing Apt (a very capable package manager) with your memory.

---

### Post by Zill on 2008-11-12
arunprasad13:  Compiling from source *is* possible but, I suggest, is for advanced users only.  I have tried it in the past but it is not something I would recommend to a newbie.

It should also be unneccessary with an advanced distro like Ubuntu, when all the package management and installation is taken care of for you.

If you *do* choose to compile from source then be aware that you are highly likely to end up in "dependency hell", where each application depends on another application which depends on another application etc etc etc...

IMHO, upgrading to either Hardy (8.04) or Intrepid (8.10) is a much better option. :-)

---

### Post by arunprasad13 on 2008-11-13
though i m going to upgrade my ubuntu rather than going for source compilation and all..nevertheless i wud like to know how to do this compilation stuff just for knowledge sake..so that i can break this jinx of being a newbie..i wud be  deeply greatful if any one of you cud explain me that ..

---

### Post by Zill on 2008-11-13
arunprasad13:  You should appreciate that installing from source is deprecated in Ubuntu.  The standard package management tools take care of installing all the dependencies that would otherwise have to be done manually.  They also ensure that versions of programs are compatible with each other which, again, is difficult to do when installing from source code.

If you do want to experiment with compilation then Google will give you as much information as you require.  I got 6,160,000 hits when searching for "compiling from source".  Just be aware that you may well break your system!

---

### Post by spibou on 2008-11-13
Here are the steps for compiling something from source:

1) You find the homepage of the programme(s) you want to download.

2) You follow the instructions on the homepage in order to find the download section. If the creators of the programme have decided to make source code available there will be an option to download source in the download section. Ubuntu repositories also contain source code.

3) You create a directory under your home directory, preferably with the name of the programme. You download the source and put it in that directory.

4) It will likely be a single compressed file, let's call it programme.tar.gz If it doesn't end in tar.gz or it's more than 1 file ask here for advice.

5) If it ends in tar.gz you do ```
gzip -dc programme.tar.gz | tar xf -
```

6) Now there will be a directory available apart from the file programme.tar.gz You go to that directory.

7) In the directory there will be a file README. You read this file and it will give you instructions on how to compile. If it doesn't, look for a file INSTALL. If that doesn't exist ask here.

Note that Ubuntu "out of the box" cannot compile anything; you will need additional libraries to compile even the simplest programme. I don't remember off the top of my head what is the minimum you need but I'm hoping someone else will chip in. If not ask [here](http://ubuntuforums.org/forumdisplay.php?f=44). So when you upgrade, download all this stuff which is needed for compiling, for example packages like automake1.9, make, libc6-dev, libstdc++6-4.1-dev, linux-libc-dev, libncurses5-dev, libncursesw5-dev etc. Once you have those you are ready for your first compile. I suggest trying [bsdgames](http://packages.ubuntu.com/dapper/games/bsdgames). It has very few dependencies so it is likely that things will go completely smoothly. The games (and utilities) themselves are simple but quite entertaining and useful. I use the wtf utility all the time. Do not download the package itself, the point is that you will compile and install from source. You will see on the right of the page that there is a link for the source. You start with that and follow the steps I gave above. I have essentially covered steps 1 and 2. One way to do step 3 is ```
mkdir ~/bsdgames && pushd ~/bsdgames &&
wget 'http://archive.ubuntu.com/ubuntu/pool/universe/b/bsdgames/bsdgames_2.17.orig.tar.gz'
```
(If you don't have wget download the package)

Good luck.

---

### Post by spibou on 2008-11-13
> **Zill said:**
> arunprasad13:  You should appreciate that installing from source is deprecated in Ubuntu.
No it isn't. How did you get that idea?
> Just be aware that you may well break your system!
This sounds like FUD to me, how would he break his system?

---

### Post by jimv on 2008-11-13
Ok, the BEST thing for you to do right now is to backup your home folder, along with anything else you want to save, and do a new installation of Ubuntu 8.04.  And by "new installation", I mean that you format the drive during the install, so all the old stuff is gone.

If you do anything else, you're probably going to end up with even more problems and headaches.

---

### Post by Zill on 2008-11-13
spibou:  Apart from the problems of version control and "dependency hell" when installing from source, the other main problem is that the apt package management system does not "know" about software installed by other methods.

As Ubuntu has periodic security updates for packages, the lack of version control with compiled software, and its dependencies, means that these can get out of sync with the packaged applications.  This can lead to various problems, including system breakage.

I accept that it *may* be possible for an experienced user to resolve these problems, but IMHO this will be quite daunting to a newbie.

---

### Post by spibou on 2008-11-13
Can you give a specific scenario of how it would lead to system breakage?

---

### Post by teddks on 2008-11-13
> **spibou said:**
> Can you give a specific scenario of how it would lead to system breakage?

If you installed (through source, manually) a library which another application uses, then changes in that library could cause breakage in those applications.

It's also a huge b**ch to get some things to compile; but these things tend to be quite essential. It's much easier just to use the package manager, and in most cases, you should be able to. When you can't, installing something from source is usually just 
[list=#]
[*]download the source tarball from the distribution site
[*]extract sources
[*]in terminal, cd into the source directory and
[*]```
./configure && make && sudo make install
```
[/list]

./configure invokes a shell script which gets the build environment ready for building, make compiles the application, and sudo make install installs it. Before compiling anything, you'll need to install the 'build-essential' package.

---

### Post by Zill on 2008-11-14
> **teddks said:**
> ...If you installed (through source, manually) a library which another application uses, then changes in that library could cause breakage in those applications...
Agreed!

---

### Post by arunprasad13 on 2008-11-14
I owe you a great debt of gratitude for explaining me the concepts to such depth.thanks buddies.

---

### Post by teddks on 2008-11-25
> **spibou said:**
> No it isn't. How did you get that idea?

This sounds like FUD to me, how would he break his system?

Installing things from source packages is an instance of using the "your memory" package manager. You remember what versions of everything you have installed, and remember to go cruise to the sites to check for updates. Every time you want to install something, you need to go hunt down the dependencies, and hunt down their dependencies, and so on, until you build the full dependency tree. You also have to check every other thing that depends on any dependencies you'd be updating to see if they'd break if a newer version of a library was installed.

By contrast, the default package manager in Ubuntu is Apt. It does all of that for you, and it can't forget. The downside is that you have to rely on the repositories for programs, so sometimes you aren't running bleeding-edge. You are, however, always running stable, tested code.

Hence, the "your memory" package manager is deprecated in favor of Apt, as it is far, far better.

How would you break your system?

[list=#]
[*] You install version 0.9.3 of libfoo. Program bar depends on .9.2 of libfoo, and breaks when you install 9.3.
[*] You install version x.y.z of a critical system package. It breaks everything by not having interoperability with the other parts of your system.
[/list]

The benefit of using Apt is that all of these breakages are tested for.

---

