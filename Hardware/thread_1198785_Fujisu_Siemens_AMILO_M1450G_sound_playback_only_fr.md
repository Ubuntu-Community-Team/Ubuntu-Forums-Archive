---
title: "Fujisu Siemens AMILO M1450G: sound playback only from audio jack but not speaker"
date: 2009-06-27
forum: Hardware
---

### Post by zhangweiwu on 2009-06-27
Fujisu Siemens AMILO M1450G have 9.04 installed.

Sound playback only from audio jack but not internal speaker. Someone on other forum posted suggestion that I should look for default output, see if it is 'internal amplifier'. I followed the suggestion with gnome-alsamixer but there is no such option 'internal amplifier'.

What do you think is the reason / what can I do to get sound working on this device? Thanks. The following are my lspci and uname output.

Furthermore is there a database where I can look up Ubuntu 9.04 compatibility before deciding to install Linux on it.

```

JMP@thelma:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
JMP@thelma:~$ uname -a
Linux thelma 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 i686 GNU/Linux


```

---

### Post by mihamtalamac on 2010-01-20
thing which worked with my Amilo m1450g is as folows:
1. go to Volume Control (right click on a speaker icon and choose 'Open Volume Control')
2. go to Playback tab
3. go to Preferences (edit/Preferences) and choose 'Surround' (maybe with your distribution it won't be Surround but something else)
4. enable it in a main window and slide volume to the max
5. Enjoy ;)

---

