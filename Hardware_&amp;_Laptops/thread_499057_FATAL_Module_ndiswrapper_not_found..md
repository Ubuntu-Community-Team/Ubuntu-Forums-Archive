---
title: "FATAL: Module ndiswrapper not found."
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by Qui on 2007-07-12
i have a rather up to date system, however, when i try to enable wireless networking i get the following error "FATAL: Module ndiswrapper not found." i have tried everything, and could really use some help. 

                                                                                                             thanks,
                                                                                                            qui.


Using Ubuntu Desktop 7.4
1GB RAM
320GB HDD
MOTHER BOARD ABIT SG-80 SERIES
CELERON D 3GHZ
CD ROM
FLOPPY

the following is a copy of my shell session:

root@SC:/home/scort02/WirelessNTWK# ls -l
-rwxrwx--- 1 root plugdev 13184 2007-07-12 01:28 ndisgtk_0.6-0ubuntu3_all.deb
-rwxrwx--- 1 root plugdev 18000 2007-07-12 01:27 ndiswrapper-common_1.38-1ubuntu1_all.deb
-rwxrwx--- 1 root plugdev 32098 2007-07-12 01:27 ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

root@SC:/home/scort02/WirelessNTWK#  sudo dpkg -i ndiswrapper-common_*.deb
(Reading database ... 88036 files and directories currently installed.)
Preparing to replace ndiswrapper-common 1.38-1ubuntu1 (using ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Unpacking replacement ndiswrapper-common ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...

root@SC:/home/scort02/WirelessNTWK#   sudo dpkg -i ndiswrapper-utils*.deb
(Reading database ... 88036 files and directories currently installed.)
Preparing to replace ndiswrapper-utils-1.9 1.38-1ubuntu1 (using ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...

root@SC:/home/scort02/WirelessNTWK#   sudo dpkg -i --force-depends ndisgtk_*.deb
(Reading database ... 88036 files and directories currently installed.)
Preparing to replace ndisgtk 0.6-0ubuntu3 (using ndisgtk_0.6-0ubuntu3_all.deb) ...
Unpacking replacement ndisgtk ...
Setting up ndisgtk (0.6-0ubuntu3) ...

root@SC:/home/scort02/WirelessNTWK# ndiswrapper -l
sis163u : driver installed
        device (0457:0163) present

root@SC:/home/scort02/WirelessNTWK#   sudo depmod -a
root@SC:/home/scort02/WirelessNTWK#   sudo modprobe ndiswrapper

FATAL: Module ndiswrapper not found.

---

### Post by Azoix on 2007-07-12
[COLOR="Blue"][B][FONT="Comic Sans MS"][SIZE="3"]I had the exact same issue arise on my IBM R31 test laptop.
Using terminal to install ndis, ndis-common, ndis-source and ndisgtk , then ndis... -l  command revealed driver installed, but modprobe came out with fatal error, module not found.
Go into Synaptic, click on search , then enter ndis as the search param. and click enter, this finds the four ndis packages, tick them all for installation, then apply, let it install, reboot, then ndis commands and modprobe should work.
The GTK interface shown in System/Administration/Windows Wireless Drivers , that is installed by ndisgtk ,  doesn't show the Netgear WG111v2 USB dongle i use here, and the LED on the Dongle itself doesn't work on Ubuntu, but the wireless is up, comes up each reboot, with only a single password entry to unlock the keyring storage and i'm online.
It shows up as wlan0 in terminal using `iwconfig` command, and i use WEP encryption aswell.[/SIZE][/FONT][/B][/COLOR]

---

### Post by Qui on 2007-07-13
i have since removed ndiswrapper and reinstalled it completely while rebooting my machine after performing each operation. nothing seems to work. however, i did notice that you said all four components in your last post, i have only the following three, can you tell me the name of the missing component. 

ndisgtk_0.6-0ubuntu3_all.deb
ndiswrapper-common_1.38-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

thanks,
qui

---

### Post by Azoix on 2007-07-13
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]The four in Synaptic are ndiswrapper-utils-1.9 , ndiswrapper-source , ndiswrapper-common and ndisgtk.
Having read the output you posted above , i think your problem lies in the fact you did not install the source codes for ndis , so the wrapper can be seen.

I posted a small tutorial on this , written from a NOOB point of view , here :
 [http://ubuntuforums.org/showthread.php?t=499084](http://ubuntuforums.org/showthread.php?t=499084) it is in regards to using Netgear USB WG111v1 and WG111v2 dongles , but the commands are universal.Just point the ndiswrapper -i /  -- install command to the folder containing the .inf file for YOUR card , and all should be hunky-dory.........
[/COLOR][/SIZE][/FONT][/B]

---

### Post by Qui on 2007-07-13
hooray, 
   its working, after a few hours(4+) of reading and trying different things i came up the following site/page: 

"&#8220;packages providing ndiswrapper-modules-1.9"
[http://packages.ubuntu.com/feisty/virtual/ndiswrapper-modules-1.9](http://packages.ubuntu.com/feisty/virtual/ndiswrapper-modules-1.9)

the packages are organized by kernel. select you kernel version and download the desired package. my understanding: they allows your kernel to talk to ndiswrapper. since  it was not installed during setup, the kernel could not find/talk to ndiswrapper when it was installed, hence the error.

Fatal: ndiswrapper not found.

nonetheless, after that, i got the latest version of ndiswrapper already compiled and packaged for ubuntu by following these links:

[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) 

the instruction on the installing them can be found here along with other useful tips:

[https://help.ubuntu.com/community/wifidocs/driver/ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/wifidocs/driver/ndiswrapper?highlight=%28ndiswrapper%29)

i installed the module mentioned above followed by the additional three packages and its been working ever since. i must say that i am very pleased. 

thank you very much,
qui

ps: sorry, i did not get to try you last suggestion.

---

