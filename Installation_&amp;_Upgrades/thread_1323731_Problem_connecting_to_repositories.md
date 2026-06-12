---
title: "Problem connecting to repositories"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by faust99 on 2009-11-12
I've not been able to run > sudo apt-get update succesfully for two days now, and am wondering where the issue may be. The output is constantly:

> Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_AU                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_AU                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_AU              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_AU                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_AU              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_AU            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_AU      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_AU        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_AU            
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,347B]                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_AU        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_AU     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_AU       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_AU     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Translation-en_AU     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Translation-en_AU           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Translation-en_AU     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Translation-en_AU       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [9,347B]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages       
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages            
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages      
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages        
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages      
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages           
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages     
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages       
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages     
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/restricted Packages     
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/main Packages           
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/multiverse Packages     
  404  Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-proposed/universe Packages       
  404  Not Found
Err [http://ftp.ncnu.edu.tw](http://ftp.ncnu.edu.tw) jaunty-security Release.gpg                         
  Cannot initiate the connection to ftp.ncnu.edu.tw:80 (2001:e10:6840:12::52). - connect (101: Network is unreachable) [IP: 2001:e10:6840:12::52 80]
Err [http://ftp.ncnu.edu.tw](http://ftp.ncnu.edu.tw) jaunty-security/main Translation-en_AU
  Cannot initiate the connection to ftp.ncnu.edu.tw:80 (2001:e10:6840:12::52). - connect (101: Network is unreachable) [IP: 2001:e10:6840:12::52 80]
Err [http://ftp.ncnu.edu.tw](http://ftp.ncnu.edu.tw) jaunty-security/restricted Translation-en_AU
  Cannot initiate the connection to ftp.ncnu.edu.tw:80 (2001:e10:6840:12::52). - connect (101: Network is unreachable) [IP: 2001:e10:6840:12::52 80]
Fetched 19.3kB in 2min 0s (160B/s)              
Reading package lists... Done
W: Failed to fetch [http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/dists/jaunty-security/Release.gpg](http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/dists/jaunty-security/Release.gpg)  Cannot initiate the connection to ftp.ncnu.edu.tw:80 (2001:e10:6840:12::52). - connect (101: Network is unreachable) [IP: 2001:e10:6840:12::52 80]

W: Failed to fetch [http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/dists/jaunty-security/main/i18n/Translation-en_AU.bz2](http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/dists/jaunty-security/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to ftp.ncnu.edu.tw:80 (2001:e10:6840:12::52). - connect (101: Network is unreachable) [IP: 2001:e10:6840:12::52 80]

W: Failed to fetch [http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_AU.bz2](http://ftp.ncnu.edu.tw/Linux/ubuntu/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to ftp.ncnu.edu.tw:80 (2001:e10:6840:12::52). - connect (101: Network is unreachable) [IP: 2001:e10:6840:12::52 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release](http://archive.ubuntu.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release](http://packages.medibuntu.org/dists/karmic/Release)  Unable to find expected entry  free/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ppa.launchpad.net/mactel-support/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mactel-support/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mactel-support/ubuntu/dists/karmic/main/source/Sources.gz](http://ppa.launchpad.net/mactel-support/ubuntu/dists/karmic/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


Has anybody had similar issues? I don't know whether it is a problem with my network or whether there are server issues? It's very frustrating (obviously ;)). Some words of advice or wisdom please....

---

### Post by MartinEve on 2009-11-12
Definitely not server issues if this is persisting; all been fine here.

1.) Check that apt is not being proxied in some way or another through a malfunctioning proxy.

2.) Post the contents of your /etc/apt/sources.list file

---

### Post by asalapi on 2010-10-18
> **MartinEve said:**
> Definitely not server issues if this is persisting; all been fine here.

1.) Check that apt is not being proxied in some way or another through a malfunctioning proxy.

2.) Post the contents of your /etc/apt/sources.list file

I am having the same problems after upgrading from Lucid to Maverick.
I tried four different repositories with no luck, and Synaptic is configured to direct access to Internet.
I am totally lost. I am on the verge of reinstalling from scratch but I wouldn't like to lose my customizations, Matlab, VMplayer, ...

---

### Post by asalapi on 2013-01-21
In my case it was a corrupt locale. cd usr/lib/locale, mv locale-archive locale-archive.old, sudo dpkg-reconfigure locales solved that and many other problems (scripts using sed were getting crazy). I don't know why the locales got corrupted on upgrade, but...

---

### Post by oldos2er on 2013-01-21
Old thread closed.

---

