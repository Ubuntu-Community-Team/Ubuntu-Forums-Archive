---
title: "dell m1210 &amp; nvidia breaks sound?"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by mr19 on 2009-10-23
Hi all -

Installed jaunty on my Dell M1210.  Everything was working great until I decided to install the nvidia drivers so I could run the Compiz wm.  

In installed the 'NVidia binary X.Org driver ('version 173' driver)' package and since then my sound no longer works and I have had the occasional wifi drop (although that may have been present prior).

Here is what I found in /var/log/messages as well as the output of lspci.

TIA,
Marc

```

Oct 23 08:45:01 mrossi-laptop pulseaudio[3342]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Oct 23 08:45:01 mrossi-laptop pulseaudio[3342]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 23 08:45:01 mrossi-laptop pulseaudio[3342]: module-alsa-source.c: Your kernel driver is broken: it reports a volume range from 20.00 dB to 20.00 dB which makes no sense.

```
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 0a)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

```

---

### Post by lol768 on 2010-01-16
I am having the same problem. As soon as I installed the nvidia drivers for my card the sound broke. Any Ideas?

EDIT: If you are having this problem (whereby you install the nvidia drivers and your sound breaks) try the following:
Install the gnome alsa mixer (type "sudo apt-get install gnome-alsamixer" in the console, without the quotes) and run it by using the menu (Sound & Video ->> GNOME ALSA Mixer) or by typing gnome-alsamixer into the console. 

Once the window is open try enabling/disabling independent HD and unmuting the front audio control. This fixed the problem for me, note that I installed the 185 (To download visit: [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)) driver package and I haven't tested the latest (190?) version. It may work with the latter, but if not try downgrading to 185 (just download, chmod and run and it will remove the later verison).

---

