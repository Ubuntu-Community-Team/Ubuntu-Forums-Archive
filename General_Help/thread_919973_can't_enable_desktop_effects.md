---
title: "can't enable desktop effects"
date: 2008-09-14
forum: General Help
---

### Post by WildeBeest on 2008-09-14
This is what I get when I type compiz in a terminal.

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:002d (rev 15) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

Can anyone help?

---

### Post by chewearn on 2008-09-14
You don't have 3D graphics available.  What graphics chip do you have?

---

### Post by knattlhuber on 2008-09-14
Please type

```
lspci

```
in a terminal window and post the output.

---

### Post by yogen on 2008-09-15
> **knattlhuber said:**
> Please type

```
lspci

```
in a terminal window and post the output.
compiz used to work finely with me...until i messed with it(in pretext of upgrading it to v0.7.6...i had 0.7.4 earlier)...i wanted to upgrade so that i could use different wallpapers with each side of the cube...but instead messed everything in installation...i tried reinstalling it...but its says the same thing...i.e.-this not found checking this that...blah blah blah...

I got this output for your command 'lspci'...
yogen@yogen-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:01.0 Communication controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
yogen@yogen-desktop:~$

---

### Post by hemant123 on 2008-09-15
Is the grahpical card is necessary for enabling the  desktop effects

---

### Post by chewearn on 2008-09-15
hi yogen
Please post your problem in a separate thread, thank you.  Your problem doesn't appear to be related to the OP.

---

### Post by chewearn on 2008-09-15
> **hemant123 said:**
> Is the grahpical card is necessary for enabling the  desktop effects

You need a graphic card that has linux driver, with 3D hardware acceleration.

---

### Post by tuxxy on 2008-09-15
Compiz requires you have the correct video card driver installed

---

### Post by WildeBeest on 2008-09-15
> **chewearn said:**
> You don't have 3D graphics available.  What graphics chip do you have?

nVidia Corporation NVSM64 [RIVA TNT2 Model 64 /Model 64 Pro] (Rev 15)

This is what's displayed with lspci

I used Envy to install the driver.

It's an Old Dell Dimension 4100 that used to run WINME, trying to resurrect it for a friend.

---

### Post by WildeBeest on 2008-09-15
Stop Hijacking my thread, start your own.:mad:

---

### Post by overdrank on 2008-09-15
> **WildeBeest said:**
> Stop Hijacking my thread, start your own.:mad:

Hi and please do not try to moderate. :) You can use the report button but the user has already been ask to make their own thread by chewearn.
As for your graphics card I do not believe it will support the effects.

---

### Post by chewearn on 2008-09-16
> **WildeBeest said:**
> nVidia Corporation NVSM64 [RIVA TNT2 Model 64 /Model 64 Pro] (Rev 15)

This is what's displayed with lspci

I used Envy to install the driver.

It's an Old Dell Dimension 4100 that used to run WINME, trying to resurrect it for a friend.


I can't find any specification on that graphics card; I guess it is too old and don't have the necessary 3D acceleration.

---

### Post by knattlhuber on 2008-09-16
> **chewearn said:**
> I can't find any specification on that graphics card; I guess it is too old and don't have the necessary 3D acceleration.

Would that help?
[http://en.wikipedia.org/wiki/RIVA_TNT2]("http://en.wikipedia.org/wiki/RIVA_TNT2")

---

### Post by chewearn on 2008-09-16
> **knattlhuber said:**
> Would that help?
[http://en.wikipedia.org/wiki/RIVA_TNT2](http://en.wikipedia.org/wiki/RIVA_TNT2)

Do'h. #-o  Kick myself in the behind; totally missed Wikipedia. :oops:

Anyway, it did say in the Wikipedia page, the card support 3D.  After more advanced google-fu, I found this thread:
[http://ubuntuforums.org/showthread.php?t=310128](http://ubuntuforums.org/showthread.php?t=310128)

Basically, tseliot in post #5 said to disable composite.  Then, in post #9 was the solution.

Hope it works for you.

---

