---
title: "Volume Controls Speaker Orientation"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by sfxc13 on 2007-06-20
Instead of Controlling the volume, my volume controls speaker orienation (ie. left-right)
I am using a Dell Inspiron 9100 w/a built in subwoofer in the battery.
I have searched the forums but have yet to find a similar problem.  Any help would be greatly appreciated!
the results of lspci:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by sfxc13 on 2007-06-20
So if I use the PCM Control I can control the volume, however I cannot get the subwoofer to be totally quite.  Even with the volume at 0 I can still here the subwoofer.
Any ideas?

---

### Post by fmaste on 2007-07-01
> **sfxc13 said:**
> So if I use the PCM Control I can control the volume, however I cannot get the subwoofer to be totally quite.  Even with the volume at 0 I can still here the subwoofer.
Any ideas?

This may help. It works for me with a DELL Inspiron 9400.
Under Feisty my subwoofer is working out of the box, I believe you are using Feisty.
Open your volume control (the one near the clock by default), go to File->Change Device and make sure you have selected the one that says "Alsa Mixer". Now in Edit->Preferences check the one that says LFE and a new slider will appear to let you control your subwoofer.
The little problem is that the master volume is not working as the master one. what you can do is make then work in parallel, both Master and LFE go up and down at the same time. To do this right click on the volume icon (by default near the clock) and select Prefefences, select the one that says Alsa mixer and them select Master and by holding CTRL on you keyboard select also LFE. Now if you also want this behavior with your volume keys do the same the lower part of the device section in System->Preferences->Sound.

You can also select PCM instead of Master and LFE, play a little with the different combinations and select the one you prefer, I prefer Master and LFE.

---

