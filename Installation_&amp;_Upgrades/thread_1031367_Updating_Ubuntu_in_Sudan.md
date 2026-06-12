---
title: "Updating Ubuntu in Sudan"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by mamlouk on 2009-01-05
Hi, I went through the internet searching for anyone posting anything about updating Ubuntu in Sudan, but couldn't find anything.

However, I believe this is a Debian issue rather than an Ubuntu specific. I tried that on my locally installed Ubuntu, a Kubuntu on VBox under Vista, a Debian on VBox under Vista, and an Ubuntu server on VBox under Ubuntu.

I don't seem to have the same problem when I'm in Egypt using Egyptian servers, but I have it in Sudan using any server.

First ```
mamlouk@mamlouk-laptop:~$ uname -r
2.6.27-11-generic
```
This is an 8.10 btw.

```
mamlouk@mamlouk-laptop:~$ cat /etc/apt/sources.list
## a “general” sources.list for Hardy Heron; all sources are uncommented.

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sd.archive.ubuntu.com/ubuntu/ intrepid restricted main
deb-src http://sd.archive.ubuntu.com/ubuntu/ intrepid restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted main
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://sd.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://sd.archive.ubuntu.com/ubuntu/ intrepid universe

deb http://sd.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://sd.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://sd.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://sd.archive.ubuntu.com/ubuntu/ intrepid multiverse

deb http://sd.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://sd.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the ‘backports’
## repository.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://sd.archive.ubuntu.com/ubuntu/ intrepid-backports restricted universe multiverse main
deb-src http://sd.archive.ubuntu.com/ubuntu/ intrepid-backports restricted universe multiverse

## Uncomment the following two lines to add software from Canonical’s
## ‘partner’ repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# deb http://archive.ubuntu.com/ubuntu/ intrepid-security restricted main
# deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security restricted

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://sd.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
# deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```
I do a ```
mamlouk@mamlouk-laptop:~$ sudo apt-get update
[sudo] password for mamlouk: 
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Hit http://archive.canonical.com intrepid Release.gpg                          
Hit http://sd.archive.ubuntu.com intrepid Release.gpg                          
Get: 1 http://security.ubuntu.com intrepid-security Release.gpg [189B]         
Hit http://archive.ubuntu.com intrepid-updates/restricted Translation-en_GB    
Hit http://sd.archive.ubuntu.com intrepid/restricted Translation-en_GB         
Hit http://archive.ubuntu.com intrepid-updates/main Translation-en_GB          
Ign http://archive.canonical.com intrepid/partner Translation-en_GB            
Hit http://sd.archive.ubuntu.com intrepid/main Translation-en_GB               
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB        
Hit http://archive.canonical.com intrepid Release                              
Hit http://archive.ubuntu.com intrepid-updates Release                         
Hit http://sd.archive.ubuntu.com intrepid/universe Translation-en_GB           
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages             
Hit http://sd.archive.ubuntu.com intrepid/multiverse Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Hit http://archive.canonical.com intrepid/partner Sources                      
Hit http://archive.ubuntu.com intrepid-updates/main Packages                   
Hit http://sd.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Get: 2 http://security.ubuntu.com intrepid-security Release [44.0kB]           
Ign http://security.ubuntu.com intrepid-security Release                       
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources     
Hit http://sd.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://sd.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://sd.archive.ubuntu.com intrepid-backports Release.gpg
Hit http://security.ubuntu.com intrepid-security/main Sources
Ign http://sd.archive.ubuntu.com intrepid-backports/restricted Translation-en_GB
Ign http://sd.archive.ubuntu.com intrepid-backports/universe Translation-en_GB
Ign http://sd.archive.ubuntu.com intrepid-backports/multiverse Translation-en_GB
Ign http://sd.archive.ubuntu.com intrepid-backports/main Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://sd.archive.ubuntu.com intrepid-proposed Release.gpg              
Hit http://security.ubuntu.com intrepid-security/universe Packages          
Hit http://sd.archive.ubuntu.com intrepid-proposed/restricted Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://sd.archive.ubuntu.com intrepid-proposed/main Translation-en_GB      
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://sd.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://sd.archive.ubuntu.com intrepid-proposed/universe Translation-en_GB
Hit http://sd.archive.ubuntu.com intrepid Release       
Hit http://sd.archive.ubuntu.com intrepid-updates Release                    
Hit http://sd.archive.ubuntu.com intrepid-backports Release
Hit http://sd.archive.ubuntu.com intrepid-proposed Release
Hit http://sd.archive.ubuntu.com intrepid/restricted Packages                
Hit http://sd.archive.ubuntu.com intrepid/main Packages 
Hit http://sd.archive.ubuntu.com intrepid/restricted Sources
Hit http://sd.archive.ubuntu.com intrepid/universe Packages
Hit http://sd.archive.ubuntu.com intrepid/universe Sources
Hit http://sd.archive.ubuntu.com intrepid/multiverse Packages
Hit http://sd.archive.ubuntu.com intrepid/multiverse Sources
Hit http://sd.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://sd.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://sd.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://sd.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://sd.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://sd.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://sd.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://sd.archive.ubuntu.com intrepid-backports/main Packages
Hit http://sd.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://sd.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://sd.archive.ubuntu.com intrepid-backports/multiverse Sources
Hit http://sd.archive.ubuntu.com intrepid-proposed/restricted Packages
Hit http://sd.archive.ubuntu.com intrepid-proposed/main Packages
Hit http://sd.archive.ubuntu.com intrepid-proposed/multiverse Packages
Hit http://sd.archive.ubuntu.com intrepid-proposed/universe Packages
Fetched 190B in 4s (42B/s)
Reading package lists... Done
W: GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```
I try ```
sudo apt-get update -o Acquire::http::No-Cache=True
``` with the same output.
I remove the key from System > Administration > Software Sources > Authentication. Then I do a ```
mamlouk@mamlouk-laptop:~$ gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```
Then ```
mamlouk@mamlouk-laptop:~$ gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
OK
```
Then back to my ```
mamlouk@mamlouk-laptop:~$ sudo apt-get update
Hit http://archive.canonical.com intrepid Release.gpg
Hit http://sd.archive.ubuntu.com intrepid Release.gpg                          
Hit http://archive.ubuntu.com intrepid-updates Release.gpg                     
Get: 1 http://security.ubuntu.com intrepid-security Release.gpg [189B]         
Ign http://archive.canonical.com intrepid/partner Translation-en_GB            
Hit http://archive.ubuntu.com intrepid-updates/restricted Translation-en_GB    
Hit http://sd.archive.ubuntu.com intrepid/restricted Translation-en_GB         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB        
Hit http://archive.canonical.com intrepid Release                              
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Hit http://sd.archive.ubuntu.com intrepid/main Translation-en_GB               
Hit http://archive.ubuntu.com intrepid-updates/main Translation-en_GB          
Hit http://archive.ubuntu.com intrepid-updates Release                         
Hit http://sd.archive.ubuntu.com intrepid/universe Translation-en_GB           
Hit http://sd.archive.ubuntu.com intrepid/multiverse Translation-en_GB         
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages             
Hit http://sd.archive.ubuntu.com intrepid-updates Release.gpg                  
Hit http://archive.ubuntu.com intrepid-updates/main Packages                   
Hit http://sd.archive.ubuntu.com intrepid-updates/universe Translation-en_GB   
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources              
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Hit http://sd.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB 
Get: 2 http://security.ubuntu.com intrepid-security Release [44.0kB]           
Ign http://security.ubuntu.com intrepid-security Release                       
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://sd.archive.ubuntu.com intrepid-backports Release.gpg                
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Ign http://sd.archive.ubuntu.com intrepid-backports/restricted Translation-en_GB
Ign http://sd.archive.ubuntu.com intrepid-backports/universe Translation-en_GB 
Ign http://sd.archive.ubuntu.com intrepid-backports/multiverse Translation-en_GB
Ign http://sd.archive.ubuntu.com intrepid-backports/main Translation-en_GB     
Hit http://sd.archive.ubuntu.com intrepid-proposed Release.gpg                 
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://sd.archive.ubuntu.com intrepid-proposed/restricted Translation-en_GB
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://sd.archive.ubuntu.com intrepid-proposed/main Translation-en_GB      
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Hit http://sd.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_GB
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://sd.archive.ubuntu.com intrepid-proposed/universe Translation-en_GB  
Hit http://archive.canonical.com intrepid/partner Sources                      
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://sd.archive.ubuntu.com intrepid Release                             
Hit http://security.ubuntu.com intrepid-security/multiverse Sources           
Hit http://sd.archive.ubuntu.com intrepid-updates Release                     
Hit http://sd.archive.ubuntu.com intrepid-backports Release                  
Hit http://sd.archive.ubuntu.com intrepid-proposed Release
Hit http://sd.archive.ubuntu.com intrepid/restricted Packages
Hit http://sd.archive.ubuntu.com intrepid/main Packages 
Hit http://sd.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://sd.archive.ubuntu.com intrepid/universe Packages                    
Hit http://sd.archive.ubuntu.com intrepid/universe Sources                     
Hit http://sd.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://sd.archive.ubuntu.com intrepid/multiverse Sources                   
Hit http://sd.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://sd.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://sd.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://sd.archive.ubuntu.com intrepid-updates/multiverse Sources           
Hit http://sd.archive.ubuntu.com intrepid-backports/restricted Packages        
Hit http://sd.archive.ubuntu.com intrepid-backports/universe Packages          
Hit http://sd.archive.ubuntu.com intrepid-backports/multiverse Packages        
Hit http://sd.archive.ubuntu.com intrepid-backports/main Packages              
Hit http://sd.archive.ubuntu.com intrepid-backports/restricted Sources         
Hit http://sd.archive.ubuntu.com intrepid-backports/universe Sources           
Hit http://sd.archive.ubuntu.com intrepid-backports/multiverse Sources         
Hit http://sd.archive.ubuntu.com intrepid-proposed/restricted Packages         
Hit http://sd.archive.ubuntu.com intrepid-proposed/main Packages               
Hit http://sd.archive.ubuntu.com intrepid-proposed/multiverse Packages         
Hit http://sd.archive.ubuntu.com intrepid-proposed/universe Packages           
Fetched 190B in 10s (18B/s)                                                    
Reading package lists... Done
W: GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```
I even try ```
mamlouk@mamlouk-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mamlouk@mamlouk-laptop:~$ sudo apt-get clean all
mamlouk@mamlouk-laptop:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```
Still no luck. Is anyone else facing the same problem in Sudan?

---

