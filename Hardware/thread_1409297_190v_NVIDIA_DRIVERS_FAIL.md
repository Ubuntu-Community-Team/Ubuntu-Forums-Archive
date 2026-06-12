---
title: "190v NVIDIA DRIVERS FAIL?"
date: 2010-02-17
forum: Hardware
---

### Post by sandman3838 on 2010-02-17
Hello

I was having an issue with the 180v Nvidia installed drivers with Ubuntu 9.10.  So I thought lets update to the 190v.

The How To for installing the Drivers that I used is here (link) even though I had installed a few of the needed programs/drivers already through Synaptic:

[http://blink4blog.blogspot.com/2009/11/how-to-setup-nvidia-190-driver-in.html](http://blink4blog.blogspot.com/2009/11/how-to-setup-nvidia-190-driver-in.html)

My results are here:
******************************

kevin@Larry:~$ sudo add-apt-repository ppa:nvidia-vdpau/ppa
[sudo] password for kevin: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 71609D4D2F1518FA9C5DC0FB1DABDBB4CEC06767
gpg: requesting key CEC06767 from hkp server keyserver.ubuntu.com
gpg: key CEC06767: "Launchpad Nvidia Vdpau Team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

kevin@Larry:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys CEC06767
gpg: requesting key CEC06767 from hkp server keyserver.ubuntu.com
gpg: key CEC06767: "Launchpad Nvidia Vdpau Team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

kevin@Larry:~$ sudo apt-get update
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic Release.gpg                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/main Translation-en_US                       
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/restricted Translation-en_US                 
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/universe Translation-en_US                   
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/multiverse Translation-en_US                 
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates Release.gpg                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/main Translation-en_US               
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/restricted Translation-en_US         
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/universe Translation-en_US           
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/multiverse Translation-en_US         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security Release.gpg                         
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en_US                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                         
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/main Translation-en_US              
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/restricted Translation-en_US        
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/universe Translation-en_US          
Ign [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/multiverse Translation-en_US        
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic Release                                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates Release                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security Release                             
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/main Packages                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/restricted Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/main Sources                                 
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages [10.8kB]                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/restricted Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/universe Packages                  
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/universe Sources                       
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/multiverse Packages                    
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic/multiverse Sources                     
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/main Packages                  
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/restricted Packages            
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg                     
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/main Sources                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/restricted Sources                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/universe Packages                    
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/universe Sources                     
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/multiverse Packages                  
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-updates/multiverse Sources                   
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/main Packages                       
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/restricted Packages                 
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/main Sources                        
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/restricted Sources                  
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/universe Packages             
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/universe Sources              
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/multiverse Packages           
Hit [http://mirrors.rit.edu](http://mirrors.rit.edu) karmic-security/multiverse Sources            
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release                         
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Hit [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages                         
Fetched 77.1kB in 8s (9,308B/s)                                                
Reading package lists... Done

kevin@Larry:~$ sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings-190
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-190-modaliases is already the newest version.
nvidia-190-modaliases set to manually installed.
Package nvidia-settings-190 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nvidia-settings
E: Package nvidia-settings-190 has no installation candidate
kevin@Larry:~$ 


Any suggestion on how to get them installed?

---

### Post by sandman3838 on 2010-02-17
Check this out I tried this because it worked with another user..

"Later on, discovered that nvidia-glx-190 was available - so ran this:
sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings
That worked without errors!"

Here are the results check out the last part?


kevin@Larry:~$ sudo apt-get install nvidia-190-modaliases nvidia-glx-190 nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-190-modaliases is already the newest version.
nvidia-190-modaliases set to manually installed.
nvidia-settings is already the newest version.
The following extra packages will be installed:
  nvidia-190-kernel-source
The following packages will be REMOVED:
  nvidia-195-kernel-source
The following NEW packages will be installed:
  nvidia-190-kernel-source nvidia-glx-190
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 22.9MB of archives.
After this operation, 30.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main nvidia-190-kernel-source 190.53-0ubuntu1~karmic~nvidiavdpauppa10 [12.6MB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main nvidia-glx-190 190.53-0ubuntu1~karmic~nvidiavdpauppa10 [10.3MB]
Fetched 22.9MB in 27s (821kB/s)                                                
(Reading database ... 209415 files and directories currently installed.)
Removing nvidia-195-kernel-source ...
Selecting previously deselected package nvidia-190-kernel-source.
(Reading database ... 209223 files and directories currently installed.)
Unpacking nvidia-190-kernel-source (from .../nvidia-190-kernel-source_190.53-0ubuntu1~karmic~nvidiavdpauppa10_i386.deb) ...
Unpacking nvidia-glx-190 (from .../nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa10_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-190' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa10_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sandman3838 on 2010-02-22
**solved due to some other issues i did a reinstall of ubuntu**

---

