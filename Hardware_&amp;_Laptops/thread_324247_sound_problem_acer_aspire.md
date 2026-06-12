---
title: "sound problem acer aspire"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by schitzowolf on 2006-12-23
Hi, I'm fairly new to linux and this is my first time using ubuntu.  I have been able to get almost everything working except the sound.  Sound works fine when booting from live CD and for first session after installing to HD.  after that, Sound only comes from right speaker.  I believe this is a problem with Alsa and/or the related modules loading (or not loading) properly because when sound works, system is using alsa mixer, however after it stops working, system uses ossmixer.  I have seen several posts on other linux help sites relating to similar problems, but no solution. trying to run "alsamixer" from CLI generated this error:

```
alsamixer: function snd_mixer_load failed: Invalid argument
```

alsamixer runs fine from live CD and immediately after initial install (as expected).  I am including the output from lspci and significant portions of dmesg hoping that someone here will see something I can try to fix easily (relatively speaking)

```
scott@scott-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
```

```
$dmesg | grep alsa
/usr/local/alsa/alsa-driver-1.0.13/pci/hda/hda_codec.c:215: hda_codec: invalid dep_range_val 0:7fff
***note***  this message repeats many, many, many times

$dmesg | grep hda_codec
[   41.741694] hda_codec: num_steps = 0 for NID=0xd
again, this repeats several times!

scott@scott-laptop:~$ dmesg |grep hda-intel
[   53.921374] hda-intel: Invalid position buffer, using LPIB read method instead.
```

Also, I installed alsa 1.0.13 from source because I don't believe my card is supported (at least not completely) in v. 1.0.12rc1 (included with edgy)
any help and/or suggestions would be greatly appreciated!

---

### Post by zolly on 2006-12-24
Solution:
Open "Volume Control" and in tab "Volume", click the "chain" icon. Reduce the volume for both channel, then,  slide the volume for both channels until you start to hear sounds. You will hear the both channels.:-D 
This is bug, after restart you have to do this again.

---

### Post by schitzowolf on 2006-12-24
Thanx zolly, I should have mentiond that I already found that work around (actually, just clicking the mute button to mute the volume, then unmuting it also works).  but why does it switch from alsamixer to oss mixer?  are the errors trying to run alsamixer from the command line due to the bug or is there something on my system that needs to be fixed?

---

### Post by robi on 2006-12-25
Try this:[http://uk.360.yahoo.com/nick.white@btinternet.com](http://uk.360.yahoo.com/nick.white@btinternet.com) It worked for me on my acer aspire 5101.First install gcc and libncurses5-dev, then just follow the read me text  for manual installation.

---

### Post by schitzowolf on 2006-12-25
Thanx robi, that worked......at least partially.  I now have sound out of both speakers without adjusting the volume controls every time I reboot, however alsamixer still does not work (gives the same error).

---

