---
title: "no sound on ubuntu"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by p13 on 2005-09-01
Hi, first of all I wold like to apologize for my English, ...I'm learning. I use Ubuntu (5.04)
and I have no sound. I used to have sound in Suse 9.3. It looks like Ubuntu recognizes my sound card which is built in my motherboard, but there is silence. My motherboard is GA- GPNXP DUO. Ubuntu identifies the sound card as 82801FB/FBM/FR/FW/FRW(ICH6 Family)Hygh Definition Audio Controler. I get the following error messages related to sound:
-when I try to open “recording level monitor” = cannot connect to the sound , please run esd at a command prompt
-if I type esd and press enter I get = no such file or directory
-if I try to open “volume control” = no control volume elements and/or devices found
-george@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3e50
0000:03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:04:05.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)
0000:04:07.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
george@ubuntu:~$
 I appreciate any help, because I don't think I cannot sort it out by myself! ]
(*,)

---

### Post by felix.rommel on 2005-09-01
Maybe you have not the correct rights to use the sound card.

Can you use the sound card as root?

If yes you should add sound privileges to your user:

Go to "System" menu and then "System configuration > Users and Groups" (sorry I have a german version so it might be written differently...)

There you can add sound privileges in the right tab.

Hope that helps.

---

### Post by p13 on 2005-09-01
In sistem I have just:preference, administration, take screen shot, help, about gnome, about ubuntu,lock screen and log out.I can not finde system configuration

---

### Post by scaza on 2005-09-01
the path is system>administration>users and groups  select the user and select properties.

However I have the exact same problem,  and the user already has audio capabilites, so it must be something else.

---

### Post by scaza on 2005-09-01
I don't have a clue if this is useful at all to try, but since im new to linux and dont have any other ideas i though I would

[http://www.notebookforums.com/showthread.php?p=599961&highlight=sound#post599961](http://www.notebookforums.com/showthread.php?p=599961&highlight=sound#post599961)

They have the same card but were usuing an older version of alsa.  I already have version 1.0.8 installed with ubuntu, but I thought i'd configure it specifically with the driver they mentioned and try alsa 1.0.9.  However I can not configure it.  I get the following message:

> Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


is this impossible in ubuntu?  is there any chance it would help?

---

### Post by p13 on 2005-09-01
The user already has audio capabilites in my case too.
Thank you for the path.
No sounnnnnnn.....!!!!!! ](*,)

---

### Post by scaza on 2005-09-01
also noticed I don't have alsaconf.  Any reason for that?

---

### Post by p13 on 2005-09-01
I tried to do what they are saying, but maybe I do something wrong, it doesn't work.
I a “so new newbie”, so I cannot advise you in any way.  :grin: Sorry !!!

---

### Post by scaza on 2005-09-01
hey seems like it is a problem with ubuntu

[http://ubuntuforums.org/showthread.php?t=16454](http://ubuntuforums.org/showthread.php?t=16454)

Still looking for a solution :-x

---

### Post by scaza on 2005-09-01
hey check this out [http://ubuntuforums.org/archive/index.php/t-22696.html](http://ubuntuforums.org/archive/index.php/t-22696.html)

I was able to install it this way.

No for the moment of truth im rebooting.

---

### Post by scaza on 2005-09-09
okay that provided me a sound mixer, a recognized sound card but no actual sound

so
for those who may be interested in what stopped the silence for me:
After following many different instructions that worked for others on how to install upgrades of alsa with little success I discovered realtek driver pack
[http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True) 

you will still have to install alsa again but this makes it work for me.

It also looks like alsa-1.0.10 has much new support for HDA 880.  However I was unable to install this version for some reason.

---

