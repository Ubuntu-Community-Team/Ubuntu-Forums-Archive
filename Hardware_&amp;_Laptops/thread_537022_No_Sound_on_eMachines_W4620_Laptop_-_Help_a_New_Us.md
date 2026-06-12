---
title: "No Sound on eMachines W4620 Laptop - Help a New User!"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by thiazzi on 2007-08-28
Good day! I've just installed Ubuntu 7.04 on my eMachines W4620 laptop (dual booting with XP). Everything went fine until I had to deal with Wireless, which I fixed through browsing the forums. 

The new problem is that the sound doesn't seem to work. Videos and songs will play, I just can't  hear them through the laptop speakers or headphones.

I looked at this thread and tried it because the model is similar to mine, but it didn't work:
[http://ubuntuforums.org/showthread.php?t=261732](http://ubuntuforums.org/showthread.php?t=261732)

I'm new to linux and command line, so any help anybody might be able to provide would be very much appreciated. Help me get this working so I can leave Windows behind eventually!

---

### Post by ddrichardson on 2007-08-29
Can you post the output of lspci?

---

### Post by thiazzi on 2007-08-29
Here's the output:

```
jordan@ubuntu-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
03:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
03:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:07.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

---

### Post by ddrichardson on 2007-08-29
I haven't come across this particulaer card (ATI SB400 AC '97) but there are things that you can try. Firstly several cards are known to have odd behaviour with the volume controls - open the sound applet preferences and ensure that all the switches are available and that nothing is muted.

If this doesn't help then try muting IEC958.

There are two other suggestions I've seen for this card - one is to use the Intel HDA drivers - see [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29#head-f03da7a273788adb609b3fa7484699cb6f8a7253") howto, personally I think this is for the 450 series cards and probably wont help.

The other suggest disabling the modem if not needed. This works with some other eMachines Laptops using a similar chipset by nVidia, although obviously you lose the modem.

---

### Post by GonzalitoUY on 2007-09-24
Got the same issue and I've tried almost everything except modem disabling
How can I do it (yep, I'm a rookie)

---

