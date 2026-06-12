---
title: "HP2133 graphic problems"
date: 2010-12-29
forum: Hardware
---

### Post by robertredford on 2010-12-29
hi,
i have an HP 2133 - modele FU350 (max res.: 1024x600) with ubuntu 10.10 version - graphic chipset: VIA Chrome9 HC
(hardware description : [manual]("http://h20195.www2.hp.com/V2/GetDocument.aspx?docname=4AA1-8048EEE&doctype=data%20sheet&doclang=EN_GB&searchquery=Laptop%20and%20Tablet%20PCs/HP%202133%20Mini-Note%20PC/FU350EA&cc=emea_middle_east&lc=en") page n°2)
i have 2 problems:
-3d does not working (compiz doesn't want to install cause no hardware capabilities found)
-when i connect an external screen and i play a video with totem or vlc, the video is ok on my internal screen but not on the external (just a black square instead of the video)


So i think that is not the good driver (openchrome by default) and i need to install the VIA driver to have all functionalities.

I had downloaded and unzipped the via driver from their website but i don't know how install this under ubuntu ([link]("http://linux.via.com.tw/")) , also ubuntu hadn't xorg.conf by default.

lscpi command return this:
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5372
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
07:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

someone can help me to install this driver and create the xorg.conf please?

---

### Post by IcarusR on 2010-12-29
Assuming you downloaded the 'Driver GFX Beta' .tar.gz from the via site open this file (VIA Linux GFX Driver User Guide) with Firefox...

/5.75.32.87a-u1004-55689/VIA Linux GFX Driver User Guide/_index.html

Then goto  'Installing the VIA Linux Graphics Driver' page.

There are instructions there. I believe it installs a basic xorg.conf as part of the install. There are instructions howto modify xorg.conf & samples as part of the 'VIA Linux GFX Driver User Guide'

Beware VIA grafix are known for not working well under linux & it may not work any better with this driver installed.

---

### Post by robertredford on 2010-12-30
Thanks, i tried it, but when i reboot gnome does not launching, i'm just in front of the the log session under the terminal window ... i can log and navigate through the directories but gnome doesn't start, if i remove the drivers via the unistalltion process , gnome is launching on reboot.

If i type 'startx' i have this message :  ... dlopen : ... via_drv.so : undefined symbol : miEmptyData
Failed to load ...via_drv.so
Failed to load modle "via" (loader failed, 7)
No drivers available
Fatal server Error: no screen found

 ... an idea ???

---

### Post by IcarusR on 2010-12-30
Sounds like a bug in the driver.

Try reading this thread it is about Via grafix on a Samsung NC20, but does explain how to install drivers on non NC20. Unfortunately it is 58 pages !

[http://ubuntuforums.org/showthread.php?t=1079314]("http://ubuntuforums.org/showthread.php?t=1079314")

Or skip it & download via_chrome9_drv_u1010_v2.zip from here (post 529 of above thread.)

[http://ubuntuforums.org/showpost.php?p=10062021&postcount=529]("http://ubuntuforums.org/showpost.php?p=10062021&postcount=529")

& follow the instructions in this post (post 546 of above thread.)

[http://ubuntuforums.org/showpost.php?p=10085926&postcount=546]("http://ubuntuforums.org/showpost.php?p=10085926&postcount=546")

Good luck.

---

### Post by Red3 on 2011-03-06
^-- This works well.  Thank you IcarusR.

I just tested this on a 2133 and can confirm it works.  

(Note:  I did use different xorg.conf settings however, so YMMV - but the above posts are the right direction to take)

---

