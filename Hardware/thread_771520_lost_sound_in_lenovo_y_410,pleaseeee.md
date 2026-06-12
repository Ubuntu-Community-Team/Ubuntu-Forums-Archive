---
title: "lost sound in lenovo y 410,pleaseeee"
date: 2008-04-27
forum: Hardware
---

### Post by sinnr on 2008-04-27
hi ppl ..i am a newbie and i have recently installed hardy 8.04 lts, and found it great...i have messed up my os now ...i had initially suffered from the lack of sound ..but surprisingly after some tweaking unknowingly ....there is sound !!! i had enjoyed a lot ....but my surprise is short lived ....after i rebooted after some time ...i am again depressed to find that the sound is gone ...please help me out guys..thanks in advance .here is my output of lspci..i ll post any info if required ...thanking you .

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by ShiDi DaS on 2008-04-28
yerp.. mine too.. i'm using lenovo as well..

details :

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)


any help with all the guys using lenovo pc/laptop out there??

---

### Post by tlcrepairs on 2008-04-29
Hi guys, I have lenovo y510 and have sound but very low output until suspend/resume then i have no sound at all, any ideas? Hardy 8.04
Everything else works great, even bluetooth.



keep your face to the sun and you will never see your shadow!

---

### Post by jbernardo on 2008-04-29
Hi,
For the intel chipsets, the problem might be[ bug #192382]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/192382"), check if the workarounds there work for you. For the nvidia chipset there are also a couple of posts on that bug that might help.

---

### Post by eraserpt on 2008-04-29
Try editing your file "/etc/modprobe.d/alsa-base" and add the following line to the end if it doenst exist:
options snd-hda-intel model=lenovo

Reboot and you should be fine :)

---

### Post by gabz8472 on 2008-05-19
I also just finished setting up Hardy in my Lenovo Y410. Try this site

[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html](http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html)

It worked for me. My sound is now up and about everytime I boot up.

---

### Post by jalanbuntu on 2008-05-20
> **gabz8472 said:**
> I also just finished setting up Hardy in my Lenovo Y410. Try this site

[http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html](http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html)

It worked for me. My sound is now up and about everytime I boot up.

Does your sound also works through the output jack? Or just using laptop speakers? I still cant make my sound works through the output jack :(

---

