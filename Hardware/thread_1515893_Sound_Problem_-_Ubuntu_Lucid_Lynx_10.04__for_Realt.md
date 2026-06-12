---
title: "Sound Problem - Ubuntu Lucid Lynx 10.04  for Realtek ID 665 on Dell Studio"
date: 2010-06-23
forum: Hardware
---

### Post by black2blacky on 2010-06-23
[SIZE=2]:KSTo do this, we must begin by determining our version of alsa as follows :

> cat /proc/asound/versionAdvanced Linux Sound Architecture Driver Version 1.0.21.[/SIZE]  

 [SIZE=2]:KSTo avoid problems during the upgrade of Alsa-utils, we need to stop it with the following command :[/SIZE]
 [SIZE=2]> sudo /etc/init.d/alsa-utils stop  [/SIZE]


[SIZE=2]:KSWe must then install the necessary tools to compile along with the kernel headers :[/SIZE][SIZE=2](be patient it may take few hours if your internet speed is low, but hope it)
[/SIZE][SIZE=2]> sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev[/SIZE]
[/QUOTE][SIZE=2]
:KSThen, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils :[/SIZE]
 [SIZE=2]> cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2) [/SIZE]

 [SIZE=2]:KSAfter that, we create a new folder for the compilation and installation of the 3 files. Then, we move the 3 tar files that we just downloaded in this folder :[/SIZE]
 [SIZE=2]> sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .[/SIZE]
 [SIZE=2]:KSUnpack the 3 tar files :[/SIZE]
 [SIZE=2]> sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*[/SIZE]
 [SIZE=2]:KSWe compile and install alsa-driver :[/SIZE]
 [SIZE=2]> cd alsa-driver*
sudo ./configure
sudo make
sudo make install[/SIZE][SIZE=2]We compile and install alsa-lib :[/SIZE]
 [SIZE=2]> cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install[/SIZE]
 [SIZE=2]We compile and install alsa-utils :[/SIZE]
 [SIZE=2]> cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install[/SIZE]
 [SIZE=2]:KSThen, we remove the 3 tar files in our personal folder that are not anymore necessary :[/SIZE]
 [SIZE=2]> rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*[/SIZE]
       [SIZE=2]Then, just restart your computer and your alsa version should be 1.0.23![/SIZE]
 [SIZE=2]You can verify that you have now indeed have this version of alsa :[/SIZE]
 [SIZE=2]> cat /proc/asound/versionAdvanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May  2 2010 for kernel 2.6.32-21-generic (SMP).[/SIZE]
 [SIZE=2]Just to be sure everything is well configured, execute this command :[/SIZE]
 [SIZE=2]> sudo alsaconf[/SIZE]


[SIZE=2]
[/SIZE]

---

### Post by black2blacky on 2010-06-23
[SIZE=4]:lolflag::KSThis Procedure Works for me in my Dell Studio 1450 in Lucid lynx 10.04 64 bit too and in my girl's 32bit lucid lynx on same brand[/SIZE].:KS:lolflag:

---

### Post by black2blacky on 2010-06-23
[SIZE=3]Continue with this post for stop the speaker from blowing when the headphone jack is pluged in 

:popcorn:
:KS> [http://ubuntuforums.org/showthread.php?p=9498781#post9498781](http://ubuntuforums.org/showthread.php?p=9498781#post9498781)[/SIZE]:KS

---

### Post by castle49 on 2012-01-12
I am an absolute beginner with Ubuntu, and I want to say thank you for this detailed step-by-step explanation.  You even had the commands to change the directories, and this was SO helpful.  This worked, first try!!!!!   :)   The sound did not work AT ALL before updating, and now it's good.  

I'm running Lucid 10.04 on a Compaq Presario CQ57, uses Realtek audio.  

THANKS AGAIN!!!!  :D

---

