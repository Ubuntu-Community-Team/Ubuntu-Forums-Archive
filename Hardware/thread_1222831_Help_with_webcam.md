---
title: "Help with webcam"
date: 2009-07-25
forum: Hardware
---

### Post by azmo35 on 2009-07-25
Hi,hello to all,but i need help with tis webcam criative live cam model vf0470 to work with my Ubuntu 8.04lts.
This is what i found so far,
[http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcams/AllItems.aspx)
[http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource)
[http://overtag.dk/wordpress/2008/07/creative-live-cam-on-ubuntu-804-using-ov51x-jpeg/](http://overtag.dk/wordpress/2008/07/creative-live-cam-on-ubuntu-804-using-ov51x-jpeg/)
i been trying the steps of the last link but without success,any help will be appreciated,many thanks,azmo.> azmo@azmo-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
azmo@azmo-laptop:~$ sudo apt-get update
[sudo] password for azmo: 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                             
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB [19.6kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB [1956B] 
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB [4368B]   
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB [36.1kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Fetched 62.0kB in 0s (73.1kB/s)
Reading package lists... Done
azmo@azmo-laptop:~$ apt-get install ov51x-jpeg-source module-assistant
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
azmo@azmo-laptop:~$ sudo apt-get install ov51x-jpeg-source module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ov51x-jpeg-source is already the newest version.
module-assistant is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
azmo@azmo-laptop:~$ sudo module-assistant a-i ov51x-jpeg

Updated infos about 1 packages
Getting source for kernel version: 2.6.24-24-generic
Kernel headers available in /usr/src/linux-headers-2.6.24-24-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/ov51x-jpeg.tar.bz2, please wait...
"/usr/share/modass/packages/default.sh" build KVERS=2.6.24-24-generic KSRC=/usr/src/linux KDREV=2.6.24-24.56 kdist_image
Done with /usr/src/ov51x-jpeg-modules-2.6.24-24-generic_1.5.4-1ubuntu0.1+2.6.24-24.56_i386.deb .
dpkg -Ei /usr/src/ov51x-jpeg-modules-2.6.24-24-generic_1.5.4-1ubuntu0.1+2.6.24-24.56_i386.deb 
Selecting previously deselected package ov51x-jpeg-modules-2.6.24-24-generic.
(Reading database ... 147196 files and directories currently installed.)
Unpacking ov51x-jpeg-modules-2.6.24-24-generic (from .../ov51x-jpeg-modules-2.6.24-24-generic_1.5.4-1ubuntu0.1+2.6.24-24.56_i386.deb) ...
Setting up ov51x-jpeg-modules-2.6.24-24-generic (1.5.4-1ubuntu0.1+2.6.24-24.56) ...


---

### Post by azmo35 on 2009-08-01
:popcorn:Hi,to all about one week ago I post this thread so because i'm not expect that people are ready to give a answer, so i tried found a solution for this problem, on my case the solution came with a upgrade to Ubuntu 9.04. If you Have this problem play with a live CD, but plug the webcam before you power the pc,when the live CD is loaded the light of the web ill be on :) i don't no if you can load Cheese on a live CD but after a clean install it work for me, i hope this help some one.:P
This is on a laptop Hp Compaq Presario V4305ea
1.5 Ghzs
1000mb memory
60gb of disk more 55gb
Intel graphics mb??

---

