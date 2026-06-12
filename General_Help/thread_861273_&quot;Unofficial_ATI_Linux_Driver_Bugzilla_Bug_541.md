---
title: "&quot;Unofficial ATI Linux Driver Bugzilla Bug 541&quot; still nof fixed after 3 years ?"
date: 2008-07-16
forum: General Help
---

### Post by Browser_ice on 2008-07-16
Today July-16 2008, I followed the instructions found at the site below, hoping to have a fully functional ATI on my Ubuntu. But I winded up on an [old bug]("http://ati.cchtml.com/show_bug.cgi?id=541") that was reported 2 years ago about a 2005 module and looking in to the reported bugs, I see it still in a NEW status and not fixed ???

**[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)**

Here are the infos I have on my bug :

**less /var/log/Xorg.0.log |grep EE**
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

(II) ATI Proprietary Linux Driver Version Identifier:8.37.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.37g1                           
(II) ATI Proprietary Linux Driver Build Date: May 25 2007 14:25:03
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.37.1.1.2.3-driver-lnx-x86-x86_64-346145

**ls -l /usr/lib/dri/ |grep fglrx_dr**i
-rw-r--r-- 1 root root 9274776 2008-06-11 06:55 fglrx_dri.so

**ls -l /usr/lib/libGL***
lrwxrwxrwx 1 root root     16 2008-05-23 18:45 /usr/lib/libGLEW.so.1.4 -> libGLEW.so.1.4.0
-rw-r--r-- 1 root root 220932 2007-07-09 13:56 /usr/lib/libGLEW.so.1.4.0
lrwxrwxrwx 1 root root     12 2008-06-26 19:55 /usr/lib/libGL.so.1 -> libGL.so.1.2
-rw-r--r-- 1 root root 642552 2008-06-11 06:55 /usr/lib/libGL.so.1.2
lrwxrwxrwx 1 root root     20 2008-05-23 18:45 /usr/lib/libGLU.so.1 -> libGLU.so.1.3.070001
-rw-r--r-- 1 root root 533352 2007-10-12 20:38 /usr/lib/libGLU.so.1.3.070001

**lspci**
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

Anyone heard anything about this ?

All I want is a fully functional ATI card on my Ubuntu 7.10 . I am not planning on using any special desktop effects.

---

### Post by markbuntu on 2008-07-16
The 8.37.6 driver is old, ATI is up to 8.6 and AIGLX works just fine from 8.4xx up but I believe they require the 2.6.24 Kernel. You should check.

You could try the Radeon Driver but you should check at their site first to see if you need to do other things.

---

