---
title: "ASUS Xonar HDAV1.3 Slim HDMI sound output"
date: 2011-03-29
forum: Hardware
---

### Post by Sixwater on 2011-03-29
I recently upgraded my former desktop with the Asus Xonar HDAV 1.3 Slim card in hopes it could run HDMI sound output to my external reciever. When i installed Ubuntu 10.10 it did not find the actual HDMI ports. Previously i have been using debian without x-window management but i turned to ubuntu since i wanted to run XBMC and make the server run as a HTPC aswell( and me being intial lazy not setting up X and XBMC seamless on startup and just want to confirm it works ;D )

Now for my question, since i have spent the last few days searching the interwebz for greater knowledge about how to make HDMI sound output work, and i will point out what i mean with HDMI sound is sound out from soundcards via HDMI and not sound via graphic cards since i dont have a soundchip on my graphic card and i have already spent a vast sum on this card and a better HDMI cable.

Is there anyone here whom have knowledge, experience about this card and ubuntu/debian?

Is it even possible to have HDMI soundout via soundcards in Linux?

When reading about sound via HDMI in linux, i found some information pointing loosly to that HDMI must be set in the kernel and i started to look for information about how to compile a kernel and make the necessary modules be present in my system, is there such modules in the kernel that enables sound via soundcard put through HDMI in linux?

If so can someone point me to the right direction how i enable this. Also do i have to compile a newer kernel i would gladly do the job, though i would like to know how since i do want to learn =)

This is my current setup, compiled latest ALSA driver from source.

My 'aplay -l' outputs:

> root@TITAN:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Slim [Xonar HDAV1.3 Slim], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Slim [Xonar HDAV1.3 Slim], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@TITAN:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Slim [Xonar HDAV1.3 Slim], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Slim [Xonar HDAV1.3 Slim], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@TITAN:~#

and 'aplay -L' outputs:

> root@TITAN:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Slim
    Xonar HDAV1.3 Slim, Multichannel
    Default Audio Device
front:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    Front speakers
surround40:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Slim,DEV=0
    Xonar HDAV1.3 Slim, Multichannel
    IEC958 (S/PDIF) Digital Audio Output
root@TITAN:~#

version of alsa:
> root@TITAN:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 29 2011 for kernel 2.6.32-5-amd64 (SMP).

lspci outputs:
> root@TITAN:~# lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260] (rev a1)
04:07.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
04:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)


---

### Post by Sixwater on 2011-03-30
Bump.

---

### Post by cchhrriiss121212 on 2011-03-30
The guy who who wrote the driver for this card had this to say[ in 2009:]("http://www.spinics.net/linux/fedora/alsa-user/msg07956.html")
> The driver supports all hardware features, except HDMI,However, in January of this year he updated the ALSA database page for [ASUS]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus"), and [changed HDMI status]("http://www.alsa-project.org/main/index.php?title=Matrix:Vendor-Asus&diff=prev&oldid=2264") from "no support" to "untested support" with the kernel 2.6.38. Not a definite answer but it gives you something to try out.

To install the newer kernel see here:
[]("http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10")[http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10](http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10)

Once installed check aplay -l, alsamixer etc. for any changes.

---

### Post by Sixwater on 2011-03-30
> **cchhrriiss121212 said:**
> The guy who who wrote the driver for this card had this to say[ in 2009:]("http://www.spinics.net/linux/fedora/alsa-user/msg07956.html")
However, in January of this year he updated the ALSA database page for [ASUS]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus"), and [changed HDMI status]("http://www.alsa-project.org/main/index.php?title=Matrix:Vendor-Asus&diff=prev&oldid=2264") from "no support" to "untested support" with the kernel 2.6.38. Not a definite answer but it gives you something to try out.

To install the newer kernel see here:
[]("http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10")[http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10](http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10)

Once installed check aplay -l, alsamixer etc. for any changes.

Ahhh okey, well atleast its worth trying =) Thank you for the information!

---

### Post by lidex on 2011-04-03
See this:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

