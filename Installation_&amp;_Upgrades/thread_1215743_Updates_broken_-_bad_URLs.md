---
title: "Updates broken - bad URLs?"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by mscoxoh on 2009-07-17
I've seen other postings on this but couldn't find a solution. On my Gutsy server if I do apt-get update or aptitude update (or aptitude safe-upgrade) I get the below bunch of failed of fetch errors. Do I need an /etc/apt/sources.list update - if so where can I get a good one, or what should I add?

```
Ign cdrom://Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.debian.org](http://security.debian.org) etch/updates Release.gpg [835B]               
Ign [http://security.debian.org](http://security.debian.org) etch/updates/main Translation-en_US             
Ign [http://security.debian.org](http://security.debian.org) etch/updates/contrib Translation-en_US          
Hit [http://security.debian.org](http://security.debian.org) etch/updates Release                            
Err [http://security.debian.org](http://security.debian.org) etch/updates Release                            
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Get:2 [http://security.debian.org](http://security.debian.org) etch/updates Release [37.6kB]                 
Get:3 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch Release.gpg [1032B]                        
Ign [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch/main Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch Release                                      
Err [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch Release                                      
  
Ign [http://security.debian.org](http://security.debian.org) etch/updates Release                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://security.debian.org](http://security.debian.org) etch/updates/main Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Get:4 [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch Release [67.8kB]                 
Hit [http://security.debian.org](http://security.debian.org) etch/updates/contrib Packages                   
Hit [http://security.debian.org](http://security.debian.org) etch/updates/main Sources                       
Hit [http://security.debian.org](http://security.debian.org) etch/updates/contrib Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources              
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
  404 Not Found [IP: 91.189.88.140 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
  404 Not Found
Ign [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch Release                                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages              
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages           
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources            
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages         
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages   
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources          
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources    
  404 Not Found [IP: 91.189.88.140 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
  404 Not Found
Hit [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch/main Packages                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
  404 Not Found [IP: 91.189.88.140 80]
Hit [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch/main Sources 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.140 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.140 80]
Fetched 107kB in 1s (84.8kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Reading package lists... Done
W: GPG error: [http://security.debian.org](http://security.debian.org) etch/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
W: GPG error: [http://ftp.uk.debian.org](http://ftp.uk.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by vinutux on 2009-07-17
remove un-official repos from software source aka souce.list then try

---

### Post by Tibuda on 2009-07-17
As you can see in [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases), Gutsy reached its end of life, and is not supported anymore. I suggest you to try a newer version. Jaunty (9.04) is the last release and hardy (8.04) is the last long-time-support release.

---

