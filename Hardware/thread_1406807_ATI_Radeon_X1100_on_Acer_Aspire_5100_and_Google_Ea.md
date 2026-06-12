---
title: "ATI Radeon X1100 on Acer Aspire 5100 and Google Earth"
date: 2010-02-14
forum: Hardware
---

### Post by marcelovilaca on 2010-02-14
Hello everybody!!!!

I used to work with RedHat and Fedora years ago, and now I decided to get back to Linux but as an user... I've just isntalled the last Ubuntu Version 9.10 Karmic Koala and founded it just great.. everithing worked just fine... but when I installed Google Earth I started to have some problems. Nothing thath freezes my laptop or anything.. It just dont work....

Looking at thousands of foruns I sow that the problem Im having is mostly related with ATI Radeon video card. Mine is an Radeon Xpress 1100 on a Acer laptop aspire 5100 with Turion 64 1.99GHz, 4Gb memory, webcam DVD-RW and WIFI... 

I have looked on a lot of foruns and discovered that a lot of people have the same probe with Radeon X1100 but most of them solved their problem editing the xorg.conf file... this file is not present on my /etc/X11 directory. I found the /var/log/Xorg.0.log file that have some reference on some foruns, but have absolutely no idea what to do with it. 

My questions are:
Is Ubuntu 9.10 X86 32 supposed to recognize 4Gb? It is only Recognyzing 3Gb...
How can I configure my ATI video card? Can I download some premade xorg.conf??
Why is it recognizing my ATI card as an Radeon Xpress 200M?
How can I make my Google Earth to work?

This is my error message when I execute google earth:
[COLOR=Gray]
[COLOR=RoyalBlue]marcelo@Marcelo-laptop-1:~$ ./googleearth
googleearth-bin: ../../src/xcb_io.c:542: _XRead: Assertiva `dpy->xcb->reply_data != ((void *)0)' falhou.
Google Earth has caught signal 6.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/marcelo/.googleearth/crashlogs/crashlog-4b783d41.txt

Please include this file if you submit a bug report will to Google.
marcelo@Marcelo-laptop-1:~$ 
[/COLOR][/COLOR]
This is what I got when triing to install ati driver 10.1:

[COLOR=RoyalBlue]marcelo@Marcelo-laptop-1:~/Downloads$ ./ati-driver-installer-10-1-x86.x86_64.run
Created directory fglrx-install.0aHMCz
Verifying archive integrity...Error in MD5 checksums: 0ded89d908cdb6db4ab9f827286b376b is different from 19e3621a3db93d97885627c08e7e2a2b
marcelo@Marcelo-laptop-1:~/Downloads$ [/COLOR]

This is what I got when triing to install ati-driver-installer-8.443.1-x86.x86_64.run 

[COLOR=RoyalBlue]marcelo@Marcelo-laptop-1:~/Downloads$ ./ati-driver-installer-8.443.1-x86.x86_64.run 
Created directory fglrx-install.wU8dHt
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.443.1.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-19-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.wU8dHt
marcelo@Marcelo-laptop-1:~/Downloads$ [/COLOR]

Please, I need some help here!!!

Thankz 

Marcelo

---

### Post by wesleyb82 on 2010-02-15
I'm having the same issues with a Acer 3100 (almost same model). Seems like I have the open drivers working and they are not cutting the cheese for HD playback, etc. I have a conversation going in newbie forum [http://art.ubuntuforums.org/showthread.php?p=8829904&posted=1#post8829904](http://art.ubuntuforums.org/showthread.php?p=8829904&posted=1#post8829904) but im going to keep an eye over here, good luck

---

### Post by marcelovilaca on 2010-02-15
Hey Wesley, thank you very much for the reply...

I'm taking a look at the newbi conversation, let me update you on my situation...

I was able to install the ati-driver-installer-10-1-x86.x86_64.run, it seems that the old archive I had was corrupted... now it installed an ATI Catalyst Control Center on my System -> Preferencies ... but when I try to run it it tells me that there is a problem initiating ATI driver, there is no ATI driver installed or it is not working properly... tells me to run aticonfig, but when I run it I get:
[COLOR=Blue]
marcelo@Marcelo-laptop-1:~$ aticonfig
aticonfig: No supported adapters detected
marcelo@Marcelo-laptop-1:~$ [/COLOR]

When I put lspci on terminal it shows:

[COLOR=Blue]marcelo@Marcelo-laptop-1:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
marcelo@Marcelo-laptop-1:~$ [/COLOR]

I would have no problem on configuring it manually if I knew how... this apsence of xorg.conf is giving me trouble... as this destro is quite new, you dont have many answers on the web....

thank you again for helping me, I'm trying here based on that other discussion you sent me, but if you have any other ideas please post here... If I have any news I'll also post here....

---

