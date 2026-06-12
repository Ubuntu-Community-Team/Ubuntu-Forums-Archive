---
title: "Ubuntu Update Manager Errors"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by GeolLinux on 2009-03-17
Good afternoon all.

I have recently got myself up and running using Ubuntu, but have hit something of a snag....

I seem to be unable to install any updates from the Update manager, or even install some 3rd party software.

Below is the error message. Any ideas?


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


With thanks, GeolLinux

---

### Post by taurus on 2009-03-17
Close down update manager first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Therion on 2009-03-17
Open a Terminal, cut and paste the following into it:```
sudo dpkg --configure -a
sudo apt-get update 
sudo apt-get -f install
```

---

### Post by GeolLinux on 2009-03-17
I still seem to get an error at the end...

> mark@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for mark: 
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Setting up adobe-flashplugin (10.0.22.87-1) ...

Errors were encountered while processing:
 system-tools-backends
mark@ubuntu:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Reading package lists... Done
mark@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adobe-flashplugin
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 3964kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner adobe-flashplugin 10.0.22.87-2intrepid1 [3964kB]
Fetched 3964kB in 9s (400kB/s)                                                 
(Reading database ... 112360 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-1 (using .../adobe-flashplugin_10.0.22.87-2intrepid1_i386.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Setting up adobe-flashplugin (10.0.22.87-2intrepid1) ...

Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks for the very speedy reply

---

