---
title: "apt-get update failures, but no GUI to update sources"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by mferrier on 2009-01-07
Hi, I've got an old feisty ubuntu box that is getting 404s on some sources when I apt-get update. As a result, I can't install some packages. The only solution for this I've found through google is to change the sources in /etc/apt/sources.lst through the software sources panel in the GUI. Problem is, this box is just a server sitting around the office with no monitor or peripherals attached. Is there a way to fix this issue from the command line? 

Contents of sources.lst and output of apt-get update:
```

$ sudo apt-get update
Ign http://medibuntu.sos-sts.com feisty Release.gpg
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_CA                                                                           
Get:1 http://archive.canonical.com feisty-commercial Release.gpg [189B]                                                                  
Ign http://archive.canonical.com feisty-commercial/main Translation-en_CA                                                                
Get:2 http://security.ubuntu.com feisty-security Release.gpg [189B]                                                                      
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA                                                         
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_CA                                                            
Get:3 http://archive.canonical.com feisty-commercial Release [5999B]                                                    
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA                     
Ign http://security.ubuntu.com feisty-security/universe Translation-en_CA                       
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA                     
Hit http://security.ubuntu.com feisty-security Release                                          
Ign http://archive.ubuntu.com feisty Release.gpg                          
Ign http://archive.ubuntu.com feisty/main Translation-en_CA               
Ign http://medibuntu.sos-sts.com feisty Release                                                
Ign http://archive.ubuntu.com feisty/restricted Translation-en_CA                          
Ign http://archive.ubuntu.com feisty/universe Translation-en_CA      
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_CA    
Get:4 http://archive.ubuntu.com feisty-proposed Release.gpg [189B]   
Ign http://archive.ubuntu.com feisty-proposed/main Translation-en_CA 
Ign http://archive.ubuntu.com feisty-proposed/restricted Translation-en_CA
Ign http://archive.ubuntu.com feisty-proposed/universe Translation-en_CA
Ign http://archive.ubuntu.com feisty-proposed/multiverse Translation-en_CA
Ign http://medibuntu.sos-sts.com feisty/free Packages                                      
Hit http://security.ubuntu.com feisty-security/main Packages                               
Get:5 http://archive.ubuntu.com feisty-updates Release.gpg [189B]                                 
Ign http://medibuntu.sos-sts.com feisty/non-free Packages                                                               
Hit http://archive.canonical.com feisty-commercial/main Packages                                                        
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_CA                               
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_CA                         
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_CA                           
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_CA                         
Hit http://security.ubuntu.com feisty-security/restricted Packages                                
Hit http://security.ubuntu.com feisty-security/universe Packages                                  
Hit http://security.ubuntu.com feisty-security/multiverse Packages                                
Hit http://security.ubuntu.com feisty-security/main Sources                                       
Get:6 http://archive.ubuntu.com feisty-backports Release.gpg [189B]                               
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_CA                             
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_CA                       
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_CA                         
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_CA
Ign http://medibuntu.sos-sts.com feisty/free Sources                 
Hit http://security.ubuntu.com feisty-security/restricted Sources    
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Ign http://archive.ubuntu.com feisty Release   
Hit http://archive.ubuntu.com feisty-proposed Release                       
Hit http://archive.ubuntu.com feisty-updates Release                        
Err http://medibuntu.sos-sts.com feisty/free Packages                                            
  404 Not Found [IP: 8.15.7.107 80]
Hit http://archive.ubuntu.com feisty-backports Release                      
Ign http://archive.ubuntu.com feisty/main Packages                                               
Ign http://archive.ubuntu.com feisty/restricted Packages                                         
Ign http://archive.ubuntu.com feisty/universe Packages                                           
Ign http://archive.ubuntu.com feisty/multiverse Packages                                         
Ign http://archive.ubuntu.com feisty/main Sources                                                
Ign http://archive.ubuntu.com feisty/restricted Sources                                          
Err http://medibuntu.sos-sts.com feisty/non-free Packages                                        
  404 Not Found [IP: 8.15.7.107 80]
Ign http://archive.ubuntu.com feisty/universe Sources                       
Ign http://archive.ubuntu.com feisty/multiverse Sources
Hit http://archive.ubuntu.com feisty-proposed/main Packages
Hit http://archive.ubuntu.com feisty-proposed/restricted Packages
Hit http://archive.ubuntu.com feisty-proposed/universe Packages
Hit http://archive.ubuntu.com feisty-proposed/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Err http://medibuntu.sos-sts.com feisty/free Sources
  404 Not Found [IP: 8.15.7.107 80]
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Err http://medibuntu.sos-sts.com feisty/non-free Sources
  404 Not Found [IP: 8.15.7.107 80]
Hit http://archive.ubuntu.com feisty-updates/universe Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources
Err http://archive.ubuntu.com feisty/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com feisty/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com feisty/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com feisty/main Sources
  404 Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com feisty/restricted Sources
  404 Not Found [IP: 91.189.88.40 80]
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Hit http://archive.ubuntu.com feisty-backports/main Sources
Hit http://archive.ubuntu.com feisty-backports/restricted Sources
Hit http://archive.ubuntu.com feisty-backports/universe Sources
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources
Err http://archive.ubuntu.com feisty/universe Sources
  404 Not Found [IP: 91.189.88.40 80]
Err http://archive.ubuntu.com feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.40 80]
Fetched 6192B in 1s (3773B/s)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz  404 Not Found [IP: 8.15.7.107 80]
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz  404 Not Found [IP: 8.15.7.107 80]
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz  404 Not Found [IP: 8.15.7.107 80]
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz  404 Not Found [IP: 8.15.7.107 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.40 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

```

$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Listen
#deb http://theli.free.fr/packages/ feisty listen

```

---

### Post by avtolle on 2009-01-07
You are aware that there is no longer support for Feisty, as it has ended its "life", correct? The repos have been taken down.

To update the sources.list from the command line, you would need to use an editor; nano is my choice for this. At the prompt, ```
 sudo nano /etc/apt/sources.list
```will get you into the list for editing; once finished, ^O to write, ^X to exit. Hope this helps.

---

### Post by mferrier on 2009-01-07
Oh, really? I wasn't aware. So, since my apt is broken, is there a way I can upgrade to whatever from the command line?

---

### Post by avtolle on 2009-01-07
Hopefully, [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) will help you get from Feisty to Gutsy, if you are interested in doing it this way. Otherwise, you would need to download the iso for the version you want to go to, and do a fresh install after backing up the relevant files.

---

