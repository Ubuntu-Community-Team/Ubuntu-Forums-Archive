---
title: "Graphics Problem (Intrepid Ibex 8.10)"
date: 2008-12-23
forum: Hardware
---

### Post by stormeagle on 2008-12-23
Hey everyone,

I'm having a lot of trouble with my Graphics card.
When i start up i get this message
"You must run Ubuntu in Low graphics mode"
When i try to configure it or set to defaults it sets my Xorg.conf to blank
Aticonfig is a blank document

Command Prompt1
(Attempt to fix my problem

----------------
cody@cody-desktop:~$ glxgears
363 frames in 5.0 seconds = 72.473 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 943 requests (938 known processed) with 0 events remaining.      
cody@cody-desktop:~$ fgrlxconfig
bash: fgrlxconfig: command not found
cody@cody-desktop:~$ fgrlxconfig    
bash: fgrlxconfig: command not found
cody@cody-desktop:~$ glxgears    
750 frames in 5.0 seconds = 149.989 FPS
735 frames in 5.0 seconds = 146.872 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 3295 requests (33 known processed) with 0 events remaining.      
cody@cody-desktop:~$ glxinfo |grep render                                    
direct rendering: Yes                                                        
OpenGL renderer string: Software Rasterizer                                  
cody@cody-desktop:~$ fgrlxconfig
bash: fgrlxconfig: command not found
cody@cody-desktop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:                                                                              
sudo apt-get install xorg-driver-fglrx                                          
bash: fglrxinfo: command not found                                              
cody@cody-desktop:~$ aticonfig --initiate
The program 'aticonfig' is currently not installed.  You can install it by typing:                                                                              
sudo apt-get install xorg-driver-fglrx                                          
bash: aticonfig: command not found                                              
cody@cody-desktop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for cody:                                  
Reading package lists... Done                              
Building dependency tree                                   
Reading state information... Done                          
The following extra packages will be installed:            
  fglrx-amdcccle fglrx-kernel-source                       
Suggested packages:                                        
  libamdxvba1                                                                   
The following NEW packages will be installed:                                   
  fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx                          
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.                  
Need to get 0B/20.2MB of archives.                                              
After this operation, 55.8MB of additional disk space will be used.             
Do you want to continue [Y/n]? Y                                                
Selecting previously deselected package fglrx-kernel-source.                    
(Reading database ... 419286 files and directories currently installed.)        
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.552-0ubuntu0.1_i386.deb) ...                                                                  
Selecting previously deselected package xorg-driver-fglrx.                      
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.552-0ubuntu0.1_i386.deb) ...                                                                      
Selecting previously deselected package fglrx-amdcccle.                         
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.552-0ubuntu0.1_i386.deb) ...                                                                            
Processing triggers for man-db ...                                              
Setting up fglrx-kernel-source (2:8.552-0ubuntu0.1) ...                         
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up xorg-driver-fglrx (2:8.552-0ubuntu0.1) ...

Setting up fglrx-amdcccle (2:8.552-0ubuntu0.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
cody@cody-desktop:~$ aticonfig --inituate
aticonfig: unrecognized option '--inituate'
aticonfig: parsing the command-line failed.
cody@cody-desktop:~$ aticonfig --initiate
aticonfig: unrecognized option '--initiate'
aticonfig: parsing the command-line failed.
cody@cody-desktop:~$ aticonfig --initiate
aticonfig: unrecognized option '--initiate'
aticonfig: parsing the command-line failed.
cody@cody-desktop:~$ aticonfig -initiate
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
cody@cody-desktop:~$ Hey everyone,
bash: Hey: command not found
cody@cody-desktop:~$

---

### Post by stormeagle on 2008-12-24
Graphics Card:
ATI PCI Express X1650 Radeon 512mbs

---

