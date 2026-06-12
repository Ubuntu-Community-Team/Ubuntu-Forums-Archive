---
title: "Yet Another Sound Thread"
date: 2011-12-12
forum: Hardware
---

### Post by lo'tar on 2011-12-12
Hi all,

Apologies for starting yet another thread about sound problems but I've been going around in circles now for a while and thought I'd try and get some expert advice.

I installed Ubuntu 11.04 (the current download) alongside Windows XP.  Everything appears to work fine, including my graphics drivers, however, I  have no sound whatsoever.

I have read a number of posts and guides and have attempted to follow the troubleshooting guide here: - [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting).

Some of the results have been: -

                          [PHP]xxxxxx@xxxxx-MS-7253:~$ aplay -l | grep card 
 aplay: device_list:240: no soundcards found... 
 xxxx@xxxx-7253:~$ sudo aplay -l 
 [sudo] password for xxxxxx:  
 aplay: device_list:240: no soundcards found...[/PHP]and 

 ```
xxxx@xxxxx-MS-7253:~$ lspci -v | grep -A7 -i "audio" 
 80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10) 
     Subsystem: Micro-Star International Co., Ltd. Device 7253 
     Flags: fast devsel, IRQ 17 
     Memory at <ignored> (64-bit, non-prefetchable) 
     Capabilities: <access denied> 
     Kernel modules: snd-hda-intel 
```
Everything seems to suggest that the software is there but is not functioning correctly.

Following another post, I have found my way to the alsa-project web site and found the relevant software for my sound card (it's on-board by the way) however, the guide seems to demand a level of Linux knowledge that I don't have.

Therefore, is there anybody out there than can dumb it down for me (a lot) to a point that I can follow?

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

Oh and yes, the sound is turned up, although some of the commands that I have blindly run have managed to remove the sound icon from the top right notification area!!

Any and all help greatly appreciated.

Regards

Tim

---

### Post by collisionystm on 2011-12-12
did you do this 

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

---

### Post by lo'tar on 2011-12-13
> **collisionystm said:**
> did you do this 

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)


Hi collisionystm,

Yes, I remember running those commands from that page and it didn't work.  Ran them again anyhows and this is what I get :-

                          [HTML]xxxxx@xxxxx-MS-7253:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
 [sudo] password for xxxxx:  
 You are about to add the following PPA to your system: 
  Ubuntu Audio Dev team PPA 
  This PPA will be used to provide testing versions of packages for supported Ubuntu releases. 
  More info: https://launchpad.net/~ubuntu-audio-dev/+archive/ppa 
 Press [ENTER] to continue or ctrl-c to cancel adding it 
  
 Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.JyCvRiQYIG --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5 
 gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com 
 gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported 
 gpg: Total number processed: 1 
 gpg:               imported: 1  (RSA: 1) 
 xxxxx@xxxxx-MS-7253:~$ sudo apt-get update 
 Ign http://security.ubuntu.com oneiric-security InRelease 
 Ign http://ppa.launchpad.net oneiric InRelease                       
 Ign http://ppa.launchpad.net oneiric InRelease                                  
 Ign http://extras.ubuntu.com oneiric InRelease                                  
 Ign http://gb.archive.ubuntu.com oneiric InRelease                    
 Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                      
 Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                    
 Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]           
 Hit http://ppa.launchpad.net oneiric Release.gpg                                
 Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]             
 Hit http://gb.archive.ubuntu.com oneiric Release.gpg                  
 Get:3 http://security.ubuntu.com oneiric-security Release [32.4 kB]   
 Ign http://ppa.launchpad.net oneiric Release.gpg                                
 Hit http://extras.ubuntu.com oneiric Release                                    
 Get:4 http://gb.archive.ubuntu.com oneiric-updates Release.gpg [198 B]          
 Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                  
 Hit http://ppa.launchpad.net oneiric Release                                    
 Hit http://gb.archive.ubuntu.com oneiric Release                                
 Ign http://ppa.launchpad.net oneiric Release                                    
 Get:5 http://gb.archive.ubuntu.com oneiric-updates Release [32.4 kB]   
 Hit http://extras.ubuntu.com oneiric/main Sources                               
 Ign http://ppa.launchpad.net oneiric/main TranslationIndex                      
 Hit http://gb.archive.ubuntu.com oneiric-backports Release                      
 Hit http://extras.ubuntu.com oneiric/main i386 Packages                         
 Ign http://extras.ubuntu.com oneiric/main TranslationIndex               
 Hit http://ppa.launchpad.net oneiric/main Sources                               
 Hit http://ppa.launchpad.net oneiric/main i386 Packages                         
 Ign http://ppa.launchpad.net oneiric/main TranslationIndex                      
 Hit http://gb.archive.ubuntu.com oneiric/main Sources                           
 Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                     
 Hit http://gb.archive.ubuntu.com oneiric/universe Sources                       
 Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                     
 Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                     
 Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages               
 Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                 
 Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages               
 Get:6 http://security.ubuntu.com oneiric-security/main Sources [20.6 kB]        
 Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                  
 Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex            
 Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex            
 Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex              
 Get:7 http://gb.archive.ubuntu.com oneiric-updates/main Sources [97.7 kB]       
 Get:8 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]     
 Get:9 http://security.ubuntu.com oneiric-security/universe Sources [5,590 B]    
 Get:10 http://security.ubuntu.com oneiric-security/multiverse Sources [653 B]   
 Get:11 http://security.ubuntu.com oneiric-security/main i386 Packages [60.8 kB] 
 Get:12 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,348 B] 
 Get:13 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [27.4 kB]  
 Get:14 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B] 
 Get:15 http://security.ubuntu.com oneiric-security/universe i386 Packages [16.5 kB] 
 Get:16 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [2,415 B] 
 Get:17 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [226 kB] 
 Err http://ppa.launchpad.net oneiric/main Sources                               
   404  Not Found 
 Get:18 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [1,653 B] 
 Get:19 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B] 
 Get:20 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [71 B] 
 Get:21 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B] 
 Get:22 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B] 
 Err http://ppa.launchpad.net oneiric/main i386 Packages                         
   404  Not Found 
 Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                     
 Hit http://security.ubuntu.com oneiric-security/main Translation-en             
 Ign http://extras.ubuntu.com oneiric/main Translation-en                        
 Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en       
 Hit http://security.ubuntu.com oneiric-security/restricted Translation-en       
 Hit http://security.ubuntu.com oneiric-security/universe Translation-en         
 Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                     
 Ign http://ppa.launchpad.net oneiric/main Translation-en                        
 Ign http://ppa.launchpad.net oneiric/main Translation-en_GB 
 Ign http://ppa.launchpad.net oneiric/main Translation-en  
 Get:23 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B] 
 Get:24 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [67.1 kB] 
 Get:25 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,657 B] 
 Get:26 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B] 
 Get:27 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B] 
 Get:28 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B] 
 Get:29 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B] 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/main Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en 
 Get:30 http://gb.archive.ubuntu.com oneiric-updates/main Translation-en [104 kB] 
 Get:31 http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en [2,665 B] 
 Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en 
 Get:32 http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en [41.7 kB] 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en 
 Fetched 750 kB in 1s (513 kB/s)                                     
 W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found 
  
 W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found 
  
 E: Some index files failed to download. They have been ignored, or old ones used instead. 
 xxxxx@xxxxx-MS-7253:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r) 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 E: Unable to locate package linux-alsa-driver-modules-3.0.0-14-generic 
 E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-14-generic' 
 xxxxx@xxxxx-MS-7253:~$  
[/HTML]Silly question - should (uname -r) read as my login -r?

Regards

---

### Post by collisionystm on 2011-12-13
> **lo'tar said:**
> Hi collisionystm,

Yes, I remember running those commands from that page and it didn't work.  Ran them again anyhows and this is what I get :-

                          [HTML]xxxxx@xxxxx-MS-7253:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
 [sudo] password for xxxxx:  
 You are about to add the following PPA to your system: 
  Ubuntu Audio Dev team PPA 
  This PPA will be used to provide testing versions of packages for supported Ubuntu releases. 
  More info: https://launchpad.net/~ubuntu-audio-dev/+archive/ppa 
 Press [ENTER] to continue or ctrl-c to cancel adding it 
  
 Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.JyCvRiQYIG --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5 
 gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com 
 gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported 
 gpg: Total number processed: 1 
 gpg:               imported: 1  (RSA: 1) 
 xxxxx@xxxxx-MS-7253:~$ sudo apt-get update 
 Ign http://security.ubuntu.com oneiric-security InRelease 
 Ign http://ppa.launchpad.net oneiric InRelease                       
 Ign http://ppa.launchpad.net oneiric InRelease                                  
 Ign http://extras.ubuntu.com oneiric InRelease                                  
 Ign http://gb.archive.ubuntu.com oneiric InRelease                    
 Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                      
 Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                    
 Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]           
 Hit http://ppa.launchpad.net oneiric Release.gpg                                
 Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]             
 Hit http://gb.archive.ubuntu.com oneiric Release.gpg                  
 Get:3 http://security.ubuntu.com oneiric-security Release [32.4 kB]   
 Ign http://ppa.launchpad.net oneiric Release.gpg                                
 Hit http://extras.ubuntu.com oneiric Release                                    
 Get:4 http://gb.archive.ubuntu.com oneiric-updates Release.gpg [198 B]          
 Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                  
 Hit http://ppa.launchpad.net oneiric Release                                    
 Hit http://gb.archive.ubuntu.com oneiric Release                                
 Ign http://ppa.launchpad.net oneiric Release                                    
 Get:5 http://gb.archive.ubuntu.com oneiric-updates Release [32.4 kB]   
 Hit http://extras.ubuntu.com oneiric/main Sources                               
 Ign http://ppa.launchpad.net oneiric/main TranslationIndex                      
 Hit http://gb.archive.ubuntu.com oneiric-backports Release                      
 Hit http://extras.ubuntu.com oneiric/main i386 Packages                         
 Ign http://extras.ubuntu.com oneiric/main TranslationIndex               
 Hit http://ppa.launchpad.net oneiric/main Sources                               
 Hit http://ppa.launchpad.net oneiric/main i386 Packages                         
 Ign http://ppa.launchpad.net oneiric/main TranslationIndex                      
 Hit http://gb.archive.ubuntu.com oneiric/main Sources                           
 Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                     
 Hit http://gb.archive.ubuntu.com oneiric/universe Sources                       
 Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                     
 Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                     
 Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages               
 Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                 
 Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages               
 Get:6 http://security.ubuntu.com oneiric-security/main Sources [20.6 kB]        
 Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                  
 Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex            
 Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex            
 Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex              
 Get:7 http://gb.archive.ubuntu.com oneiric-updates/main Sources [97.7 kB]       
 Get:8 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]     
 Get:9 http://security.ubuntu.com oneiric-security/universe Sources [5,590 B]    
 Get:10 http://security.ubuntu.com oneiric-security/multiverse Sources [653 B]   
 Get:11 http://security.ubuntu.com oneiric-security/main i386 Packages [60.8 kB] 
 Get:12 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,348 B] 
 Get:13 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [27.4 kB]  
 Get:14 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B] 
 Get:15 http://security.ubuntu.com oneiric-security/universe i386 Packages [16.5 kB] 
 Get:16 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [2,415 B] 
 Get:17 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [226 kB] 
 Err http://ppa.launchpad.net oneiric/main Sources                               
   404  Not Found 
 Get:18 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [1,653 B] 
 Get:19 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B] 
 Get:20 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [71 B] 
 Get:21 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B] 
 Get:22 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B] 
 Err http://ppa.launchpad.net oneiric/main i386 Packages                         
   404  Not Found 
 Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                     
 Hit http://security.ubuntu.com oneiric-security/main Translation-en             
 Ign http://extras.ubuntu.com oneiric/main Translation-en                        
 Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en       
 Hit http://security.ubuntu.com oneiric-security/restricted Translation-en       
 Hit http://security.ubuntu.com oneiric-security/universe Translation-en         
 Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                     
 Ign http://ppa.launchpad.net oneiric/main Translation-en                        
 Ign http://ppa.launchpad.net oneiric/main Translation-en_GB 
 Ign http://ppa.launchpad.net oneiric/main Translation-en  
 Get:23 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B] 
 Get:24 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [67.1 kB] 
 Get:25 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,657 B] 
 Get:26 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B] 
 Get:27 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B] 
 Get:28 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B] 
 Get:29 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B] 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe TranslationIndex 
 Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/main Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB 
 Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en 
 Get:30 http://gb.archive.ubuntu.com oneiric-updates/main Translation-en [104 kB] 
 Get:31 http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en [2,665 B] 
 Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en 
 Get:32 http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en [41.7 kB] 
 Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en 
 Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en 
 Fetched 750 kB in 1s (513 kB/s)                                     
 W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found 
  
 W: Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found 
  
 E: Some index files failed to download. They have been ignored, or old ones used instead. 
 xxxxx@xxxxx-MS-7253:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r) 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 E: Unable to locate package linux-alsa-driver-modules-3.0.0-14-generic 
 E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-14-generic' 
 xxxxx@xxxxx-MS-7253:~$  
[/HTML]Silly question - should (uname -r) read as my login -r?

Regards


no... uname -r just reads the kernel version you have and substitutes it into the command 

it looks like there isnt and updated version of alsa for you
Unable to locate package linux-alsa-driver-modules-3.0.0-14-generic 

So.... I guess the troubleshooting needs to go a different route than alsa

unless you compile and install alsa from their website

---

### Post by lo'tar on 2011-12-15
> **collisionystm said:**
> no... uname -r just reads the kernel version you have and substitutes it into the command 

it looks like there isnt and updated version of alsa for you
Unable to locate package linux-alsa-driver-modules-3.0.0-14-generic 

So.... I guess the troubleshooting needs to go a different route than alsa

unless you compile and install alsa from their website

..... this then brings me back to my original post, in that, I don't really understand the commands on the alsa website to download and install the sound drivers that I need and am hoping someone can simplify it for me re: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

Can anyone point out which of the commands I need to run at all?

Regards

---

### Post by collisionystm on 2011-12-15
> **lo'tar said:**
> ..... this then brings me back to my original post, in that, I don't really understand the commands on the alsa website to download and install the sound drivers that I need and am hoping someone can simplify it for me re: [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

Can anyone point out which of the commands I need to run at all?

Regards

It is trying to explain how to compile and install from source.
here is what you do....

download the file from alsa. It should be a .tar.gz

extract the .tar.gz

open up a terminal and navigate to that directory

run these commands

sudo bash

./configure

./make

./make install

modprobe snd-card-hda-intel

exit

alsamixer

make sure the card is not muted 

test for sound

---

### Post by lo'tar on 2011-12-16
Man, this is getting frustrating!!

Ok, when I try to create a directory to download the drivers I am denied permission!

I had set ubuntu to boot without a password so thought I would just change that and it would recognise me as an administrator when the computer booted up and give me the necessary rights.

Unfortunately, when I try to take the padlock off the user account to make changes it will not authenticate my password!!!!

Help!!!!!!

I only want to get the bleedin sound card running!!!!

---

### Post by collisionystm on 2011-12-16
> **lo'tar said:**
> Man, this is getting frustrating!!

Ok, when I try to create a directory to download the drivers I am denied permission!

I had set ubuntu to boot without a password so thought I would just change that and it would recognise me as an administrator when the computer booted up and give me the necessary rights.

Unfortunately, when I try to take the padlock off the user account to make changes it will not authenticate my password!!!!

Help!!!!!!

I only want to get the bleedin sound card running!!!!

lol no problem.

can you use the sudo command?

you need to set a password back on your account

---

### Post by lo'tar on 2011-12-16
> **collisionystm said:**
> lol no problem.

can you use the sudo command?

you need to set a password back on your account

Hmmmm, ok, I tried SUDO and I received a list of options so I then typed "Sudo U" which asked for a password.  I typed the password (certain I typed it correctly) but I got the response "Sorry, try again". Tried 3 times and then got told I had failed 3 times - is it locked now?

Any ideas?

EDIT - ok, tried to reset my password following this guide - [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) - however, when I retype the password I get 2 error messages: -

Passwd: Authentication token manipulation error
Passwd: Password unchanged

:-(

---

### Post by lo'tar on 2011-12-17
OK, I don't appear to be getting anywhere with this now - had ubuntu installed for a week and still not got it running properly:confused:

Is it worth me re-installing ubuntu to see if it solves the problems and if so, what is the best way of doing that?

Regards

---

### Post by lo'tar on 2011-12-18
Right, re-installed ubuntu and have now fixed the password problem - seemed the sensible thing to do.

Am now back to trying to get the sound working by using the commands from the alsa web site re: - [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

```
cd /usr/src
``` Worked ok for me

```
mkdir alsa
``` I get the message "mkdir: cannot create directory `alsa': Permission denied" so I tried it with "sudo" before it and that seemed to work after entering my password.

```
cd alsa
``` Worked


```
cp /downloads/alsa-* .
``` gives me the message - "cp: cannot stat `/downloads/alsa-*': No such file or directory"

So now I am stuck again.  Am I typing something wrong or should I be adding a directory location?

Any help appreciated please.

---

### Post by MoreOrLess on 2011-12-18
If you're trying to build alsa, this script does it: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

Make sure you install libsdl1.2-dev:
```
sudo apt-get install libsdl1.2-dev
```

---

### Post by lo'tar on 2011-12-20
> **MoreOrLess said:**
> If you're trying to build alsa, this script does it: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

Make sure you install libsdl1.2-dev:
```
sudo apt-get install libsdl1.2-dev
```

I ran the above instruction and that worked, however, I have no idea where to start with the attached script :-(

Please just assume that you need to dumb it down to the level of a 5 year old and hopefully I will be able to understand!!

Going back to my earlier thread, why do I get the message "cp: cannot stat `/downloads/alsa-*': No such file or directory" when I try to run the fourth instruction from the alsa instructions re: " cp /downloads/alsa-* .". Following the instructions on the alsa site still seems the best solution but without a fuller understanding of the instructions and what they are trying to do I am just going around in circles!!!!!!


I really, really really need some form of a basic hand holding walk  through with this I cannot understand half of what I am supposed to be  doing.


EDIT - if it helps, I ran the following from one of the many sound posts that I've trawled: -
> wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

The result of that was - [http://www.alsa-project.org/db/?f=6aeec2d03e7e015a02c05f6eef7af2cdb2935158](http://www.alsa-project.org/db/?f=6aeec2d03e7e015a02c05f6eef7af2cdb2935158)

---

### Post by The Dragon Master on 2011-12-21
So "cp /downloads/alsa-* ." doesn't work for you. I suspect the directory doesn't exist, try adding a "~" and also try an uppercase "D" i.e try 

"cp ~/Downloads/alsa-* ."

on my machine "~/" is a shorthand notation for "/home/david", on your machine "~/" will be a shorthand for "/home/yourUserName" 

by default Ubuntu set's up a "Downloads" directory in "~/", but "cd ~/downloads" won't work because directory names are case sensitive.

The "." in "cp ~/Downloads/alsa-* ." refers to what ever directory you are in, you can find this by typing "pwd" in the terminal. 

The "*" is a wild card, i.e. all files in "~/Downloads" with names starting with "alsa-" will be copied

So to summarise, "cp ~/Downloads/alsa-* ." will copy every "alsa-" file in "~/Downloads/" to what ever the current directory is (which you can know by using "pwd")

I hope that is clear enough. 

Another good command to know is "man. You can try "man cp" and "man sudo" for example ;0)

good luck
TDM

---

### Post by The Dragon Master on 2011-12-21
I am also having sound card issues (using lucid LTS on a Dell Precision laptop).

I've tried following
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)
but I get the following

david@JiaYou[david] sudo apt-get install linux-alsa-driver-modules-$(uname -r)                                                     [ 9:23AM]
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-37-generic

so no driver modeules for 2.6.32-37. If I use Synaptic the nearest I can find is "linux-backports-modules-alsa-lucid-generic", so I have that installed, but that doesn't help. I then found my system had a
"linux-backports-modules-alsa-2.6.32-37-generic" so I removed the "*-lucid-generic" version to avoid conflict and reinstalled the 2.6.32-37 version. Still no sound.

Perhaps this is helpful
david@JiaYou[david]  modinfo soundcore                                                                                             [ 9:39AM]
filename:       /lib/modules/2.6.32-37-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     51925557ECF0F2838930862
depends:        
vermagic:       2.6.32-37-generic SMP mod_unload modversions 
parm:           preclaim_oss:int


The big clue seems to be with 
david@JiaYou[david] lspci -v | grep -A7 -i "audio"                                                                                 [ 9:35AM]
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
	Subsystem: Dell Device 04a4
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at e3860000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

--
01:00.1 Audio device: ATI Technologies Inc Device aa88
	Subsystem: Dell Device 04a4
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at e3740000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

so I have 2 driver cards but access is denied to both of them. How to unblock access to at least one of them? I have checked in the BIOS and see nothing to suggest they are disabled. I have gone through all the GUIs I can find and there is no "mute" selected anywhere. So I'm not sure what to do next.

anyone got some ideas?

TDM

---

### Post by The Dragon Master on 2011-12-21
Just for the record...

david@JiaYou[david] aplay -l | grep card                                                            [10:04AM]
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]

---

### Post by The Dragon Master on 2011-12-21
My problem with the instructions on page [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) is that they don't tell you where to get recent driver files. 

If I click on the "'Download'" link on the left side of the screen and then click on "Drivers", the latest listed is "alsa-driver-1.0.22.1.tar.bz2" dated "28/12/09", so two years old. Have there seriously been no ALSA drivers released in the last 2 years? Does this mean then that any soundcards released in 2011 risks being unsupported by ALSA? Is this why if I do

lspci -v | grep -A7 -i "audio"

it shows "Capabilities: <access denied>" for both my soundcards?

TDM

---

### Post by lo'tar on 2011-12-21
> **The Dragon Master said:**
> So "cp /downloads/alsa-* ." doesn't work for you. I suspect the directory doesn't exist, try adding a "~" and also try an uppercase "D" i.e try 

"cp ~/Downloads/alsa-* ."

on my machine "~/" is a shorthand notation for "/home/david", on your machine "~/" will be a shorthand for "/home/yourUserName" 

by default Ubuntu set's up a "Downloads" directory in "~/", but "cd ~/downloads" won't work because directory names are case sensitive.

The "." in "cp ~/Downloads/alsa-* ." refers to what ever directory you are in, you can find this by typing "pwd" in the terminal. 

The "*" is a wild card, i.e. all files in "~/Downloads" with names starting with "alsa-" will be copied

So to summarise, "cp ~/Downloads/alsa-* ." will copy every "alsa-" file in "~/Downloads/" to what ever the current directory is (which you can know by using "pwd")

I hope that is clear enough. 

Another good command to know is "man. You can try "man cp" and "man sudo" for example ;0)

good luck
TDM

Hi TDM,

Tried what you suggested but I still get the same error message re: "cp: cannot stat `/downloads/alsa-*': No such file or directory"

I have bee looking on the alsa web site to see if I can find the relevant drivers and manually downlaod them but it's not to easy for me to know the correct download.  I have a via vt8251/vt8237a onboad sound card but selecting that on the alsa website just takes me to a page where the installation instructions are - I cannot find a file to download.  

I have managed to find this page on the alsa site that contains drivers - should I just download the most recent ones - they're dated 26/02/02!!

[ftp://ftp.alsa-project.org/pub/driver/](ftp://ftp.alsa-project.org/pub/driver/)

Still looking for a lot of help on this to help me resolve the lack of sound.

Thanks

---

### Post by MoreOrLess on 2011-12-21
Use the script (it does the heavy lifting for you). Follow the directions:

> 1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xzvf AlsaUpgrade-1.0.24-2.tar.gz
4. chmod +x AlsaUpgrade-1.0.24-2.sh
5. sudo ./AlsaUpgrade-1.0.24-2.sh -d
6. sudo ./AlsaUpgrade-1.0.24-2.sh -c
7. sudo ./AlsaUpgrade-1.0.24-2.sh -i
8. sudo shutdown -r 0

---

### Post by lo'tar on 2011-12-21
> **MoreOrLess said:**
> Use the script (it does the heavy lifting for you). Follow the directions:


Many thanks for that MOL:)

Now, this is probably a very stupid question and I'm probably being really really thick but, which "script" are we talking about and where do I download it from?

Apologies if that's a really basic question #-o

---

### Post by MoreOrLess on 2011-12-21
Nvm. You seem to be purposely not following directions. Good luck with your issue. Unsubscribing from thread..

---

### Post by lo'tar on 2011-12-22
> **MoreOrLess said:**
> Nvm. You seem to be purposely not following directions. Good luck with your issue. Unsubscribing from thread..

[FONT=&quot]Hey, I don't get it - which instructions am I "Purposely not following"!!!!!!

You said "1. download the script and save it somewhere" but I have no idea which "script" you are talking about - how is that "purposely not following directions"?

The only "purposely" thing that I am trying to do is solve what, under windows, would be a simple thing to accomplish - install some drivers for my onboard sound card.

As I have pointed out at numerous times during this thread, I am a complete novice to Ubuntu and Linux and things that you take to be simple and run of the mill are, for the most part, alien to me.  So please, tell me where I am going wrong and I will apologies for my lack of understanding.

If anybody else knows of any way that I can resolve my issue - which is no sound after installing Ubuntu - please please let me know, preferably in terms I can understand.[/FONT]

---

### Post by Newgirlde on 2012-01-22
> **MoreOrLess said:**
> If you're trying to build alsa, this script does it: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

Make sure you install libsdl1.2-dev:
```
sudo apt-get install libsdl1.2-dev
```


I know its been a few weeks, but I hope this will help you.

The script s/he was talking about was a script s/he linked you to earlier in the thread.

---

