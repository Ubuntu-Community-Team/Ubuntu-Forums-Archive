---
title: "What hardware configuration are you using for Ubuntu 8.04 Hardy Heron ?"
date: 2008-07-10
forum: Hardware
---

### Post by raghavan on 2008-07-10
Hi, 
Is anybody using Ubuntu Server - Hardy Heron (8.04) ? I want to know what system hardware configuration you are using ? Does it support the below hardwares ? 
1) Seagate SATA 2 Disk Drives (750 GB and 500 GB) 
2) Viewsonic monitor 22 inches (vx2255wm) 
3) Transcend memory 2gb DIMM modules (800 MHZ) 
4) ASUS motherboard P5Q - Deluxe 
5) Intel Core 2 Quad Q9300
6) Samsung DVD writer (Latest or anything before that ) 
7) Router - Linksys WRT54G or WRT54GL 
 What LAN card ? 
9) What graphics card ? (I don't need too much graphics power ) 
10) What sound card ? 

Please help me. Thanks
Regards
Raghavan
<snip>

---

### Post by jimv on 2008-07-10
All that should be just fine, except I'm not sure about the mother board.  Other people have been having problems with getting it to work in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=851342](http://ubuntuforums.org/showthread.php?t=851342)
[http://vip.asus.com/forum/view.aspx?id=20080624021821000&board_id=1&model=P5Q&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20080624021821000&board_id=1&model=P5Q&page=1&SLanguage=en-us)

As for sound and ethernet cards...if you find another motherboard, the onboard sound and LAN should be just fine.

As for a video card, you can get like an Nvidia 8600gt or 8800gt...either should work just fine and will give you decent performance for hte price.

---

### Post by forger on 2008-07-10
Fire up a live cd of Ubuntu desktop, if it works then probably it will work for the server edition too!

---

### Post by raghavan on 2008-07-11
Thanks guys,

---

### Post by Forrest319 on 2008-07-23
I have an Asus p5q and I am running into problems regardless of distro (Ubuntu, openSUSE, PCLinuxOS, Fedora).  None of them recognize the Ethernet or Sound.  And I have a problem with Linux recognizing my sata drives.  None of the live cds would recognize the drives, but SUSE was able see the drives and install via DVD (not live cd).

Drivers for both the ethernet and sound card are available from ASUS website as tar balls.  But I haven't gotten either to work yet... only tried once then got tired and went to bed.

---

### Post by raghavan on 2008-07-23
> **Forrest319 said:**
> I have an Asus p5q and I am running into problems regardless of distro (Ubuntu, openSUSE, PCLinuxOS, Fedora).  None of them recognize the Ethernet or Sound.  And I have a problem with Linux recognizing my sata drives.  None of the live cds would recognize the drives, but SUSE was able see the drives and install via DVD (not live cd).

Drivers for both the ethernet and sound card are available from ASUS website as tar balls.  But I haven't gotten either to work yet... only tried once then got tired and went to bed.
Thanks Forrest.

---

### Post by NineseveN on 2008-07-26
> **Forrest319 said:**
> I have an Asus p5q and I am running into problems regardless of distro (Ubuntu, openSUSE, PCLinuxOS, Fedora).  None of them recognize the Ethernet or Sound.  And I have a problem with Linux recognizing my sata drives.  None of the live cds would recognize the drives, but SUSE was able see the drives and install via DVD (not live cd).

Drivers for both the ethernet and sound card are available from ASUS website as tar balls.  But I haven't gotten either to work yet... only tried once then got tired and went to bed.

Ubuntu 8.04 recognized my sound just fine. Had to change the SATA option in the BIOS to ACHI for it to recognize my hard drive (WD SATA 250gb). As for the ethernet, mine has the Attansic/Atheros chip, so the following worked for me:

[http://ubuntuforums.org/showpost.php?p=5456722&postcount=19](http://ubuntuforums.org/showpost.php?p=5456722&postcount=19)

---

### Post by raghavan on 2008-07-27
Thanks NineseveN

---

