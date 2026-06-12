---
title: "Sound Card Driver"
date: 2008-10-21
forum: Hardware
---

### Post by Szat on 2008-10-21
Hey everyone,
 I have a Creative Labs X-Fi XtremeGamer sound card. It works fine in Windows Vista, but I can't find any drivers for it for Ubuntu. Do I have to use my onboard sound or can someone help me find a driver?

---

### Post by pytheas22 on 2008-10-21
Ubuntu already comes with most sound drivers built in.  On newer cards, however, you may need to manually install a driver.  Also, the problem could simply be that the system is defaulting to your onboard device.  Did you try going to System>Preferences>Sound to see if your external card is detected?

If that doesn't help, try following [this troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshooting"), which should help you figure out which driver to manually install, if necessary.

Also, you may want to try using Ubuntu 8.10 instead of 8.04 (if that's what you're on now), as it will have better support for newer sound cards.

---

### Post by Tamlynmac on 2008-10-21
Apparently this sound card will be supported by the alsa-project but a driver hasn't been released yet, see this site:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

Based on the information provided at this site "Development work has started". I guess patience is the answer in this case.

---

### Post by Szat on 2008-10-27
Since my sound card isn't compatible yet with ubuntu, I enabled my onboard sound. I selected my onboard sound codecs through the sound options, but I still can't get any sound. I have tried using the sound troubleshooting guide, but it still hasn't solved my problem. Any other suggestions?  +thanks guys

---

### Post by ardvark71 on 2008-10-27
> **Szat said:**
> Since my sound card isn't compatible yet with ubuntu, I enabled my onboard sound. I selected my onboard sound codecs through the sound options, but I still can't get any sound. I have tried using the sound troubleshooting guide, but it still hasn't solved my problem. Any other suggestions?  +thanks guys

Hi...

Did you remove the Creative card from your system? Also, could you post the results of...

```
lspci
```

Best Regards...

---

### Post by Szat on 2008-10-27
Results of lspci

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
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:06.0 Multimedia audio controller: Creative Labs SB X-Fi
03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

---

### Post by ardvark71 on 2008-10-27
> **Szat said:**
> 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
03:06.0 Multimedia audio controller: Creative Labs SB X-Fi


Hi...

It appears you didn't remove the Creative sound card from your system. My guess it's either a conflict between both of the devices or possibly Ubuntu lacks a driver for both of them. ;)

Best Regards...

---

### Post by pytheas22 on 2008-10-27
It may be simplest just to reinstall Ubuntu with your PCI sound card either removed from the machine or disabled in BIOS during the install (you could put it back in after the install is complete).  I was in a situation once where I had two sound cards but couldn't get Ubuntu to install drivers for the one I wanted to use until I removed the other one from the computer and reinstalled.  You'd think there'd be an easier solution, and there probably is, but I spent a long time trying to figure it out, and a reinstall eventually became the simplest option.

According to [this thread]("http://ubuntuforums.org/showthread.php?t=583167"), your onboard card has had support at least since Feisty, so it should definitely work.

---

