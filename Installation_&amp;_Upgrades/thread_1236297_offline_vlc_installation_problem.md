---
title: "offline vlc installation problem"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by pjpriyabrata on 2009-08-10
HI
i m very very new to ubuntu  i downloaded the file "**vlc-1.0.1.tar.bz2**" in my home folder 
then i extract  the file above named ,then using terminal window i go to the folder where the vlc file extracted then  i write"** ./configure'**
it configures when i give the command make it show a massage to me that 
[B]mak:***no target specified and no make file found .stop
[/B]then i write make install 
so the massage comes like
[B]make:*** no rule to make target 'install'.stop

[/B]but in my extracted folder there is a** make-alias **file and also an** install **file [B]
i am in great problem please help me out iven if my audio player does not get updated means its pluging 

priyabrata das
[email]pjpriyabrata@gmail.com[/email]
[/B]

---

### Post by Soul-Sing on 2009-08-10
Via synpatic packagemanager you are able to install VLC.
Remember synpatic contains 25.000 software packages!
The newest VLC version can be obtained adding a PPA source to your sources.list

---

### Post by Partyboi2 on 2009-08-10
Hi, it is a lot easier to install deb packages then it is to compile. If you don't have Internet access with your machine you can either manually download vlc deb from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=all&section=all") and double click on it to start the install process. With this method you will need to manually install all the dependencies for vlc as well, which can be found at [[COLOR=Blue]ubuntu packages[/COLOR]]("http://packages.ubuntu.com/").
Another easier method is to use [[COLOR=Blue]Keyrx[/COLOR]]("http://keryxproject.org/") to install vlc plus all its dependencies instead of having to manually find them and install them.

---

### Post by pjpriyabrata on 2009-08-10
i dont even know what is sympatic manager
 
 
then how can i install it in sympatic what is its procedure  pls  tell me 
 
again i open the link what the avove replier  provide like .deb file but in the link there is no file like .deb i didnot found ps help me 
 
priyabrata das

---

### Post by sundar_ima on 2009-11-11
> **pjpriyabrata said:**
> i dont even know what is sympatic manager
 
 
then how can i install it in sympatic what is its procedure  pls  tell me 
 
again i open the link what the avove replier  provide like .deb file but in the link there is no file like .deb i didnot found ps help me 
 
priyabrata das

use VLC offline installer. Download the package from here for ubuntu 9.10 [http://rapidshare.com/files/305466861/VLC_Offline_Installer_ubuntu_9.10.tar.gz]("http://rapidshare.com/files/305466861/VLC_Offline_Installer_ubuntu_9.10.tar.gz") and here for ubuntu 9.04 [http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz]("http://rapidshare.com/files/222292699/VLC_offline_installer.tar.gz") extract the package then go to the new folder and double click on the install.sh file --> finally select run in terminal tab. 
hope this help for you.

---

