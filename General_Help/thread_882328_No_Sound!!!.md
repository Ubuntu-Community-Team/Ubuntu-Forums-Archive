---
title: "No Sound!!!"
date: 2008-08-06
forum: General Help
---

### Post by GoluckyWalnut on 2008-08-06
Hi,
I have recently installed the latest version of ubuntu on my computer and after everything was set up I realized that I was getting no sound. After fooling with a lot of setting I have got the sound to only work in rhythmbox music player, but it will not work any other program or sound. PLEASE HELP!!!

---

### Post by braddcadd on 2008-08-06
Right click on the speaker icon in the notification area.  Select "Open Volume Control," then try to change the device.

Can you tell what device Rythmbox is using?  In the preferences or something?

Here is a good sound reference:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Crafty Kisses on 2008-08-06
> **GoluckyWalnut said:**
> Hi,
I have recently installed the latest version of ubuntu on my computer and after everything was set up I realized that I was getting no sound. After fooling with a lot of setting I have got the sound to only work in rhythmbox music player, but it will not work any other program or sound. PLEASE HELP!!!

You could try the alsamixer option, also post the following output of:
```
lspci
```

---

### Post by GoluckyWalnut on 2008-08-10
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:05.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
00:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 40)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)

---

