---
title: "No Audio with Ubuntu 9.04"
date: 2009-04-26
forum: Hardware
---

### Post by jer1990 on 2009-04-26
Hello,
I have used Ubuntu before, Ubuntu 8.10, and experienced graphics problems (the screen were too blurry) so I left it and continued using Windows, then I heard 9.04 has come out so I've installed it and now I have audio issues, but pleased to say there's no graphical issues (that I can tell so far).

I have recently installed Ubuntu 9.04 on my Packard Bell iMedia 1508 /2 using the application like installation (i.e. installing it as an application within Windows; or at least using that option from the installation menu).

I've tried all sorts including the following:

==========================================/

[http://ubuntuforums.org/showthread.php?t=1130858](http://ubuntuforums.org/showthread.php?t=1130858)
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)
[http://www.linuxquestions.org/questions/linux-hardware-18/intel-82801fbfbmfrfwfrw-ich6-family-high-definition-audio-361803/](http://www.linuxquestions.org/questions/linux-hardware-18/intel-82801fbfbmfrfwfrw-ich6-family-high-definition-audio-361803/)
[https://bugzilla.redhat.com/show_bug.cgi?id=191006](https://bugzilla.redhat.com/show_bug.cgi?id=191006)
[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

==========================================/

and still no joy. I'm really impressed by Ubuntu and would love to use it, but without audio I cannot.

I am a fairly technological savvy guy when it comes to Windows and hardware, but when it comes to Ubuntu (and Mac) I'm just a noOb that knows a few tricks.

Here's what comes up when using *lspci*.

> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 LE] (rev a1)
02:01.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

**So yeah... are there any solutions out there? Is there a way to get my audio working? **If you need to know more, let me know.

---

### Post by marconeuro on 2009-05-01
Look carefully at this thread, worked for me:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
also this: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

