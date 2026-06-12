---
title: "Microphone problem on HP8510W"
date: 2010-07-21
forum: Hardware
---

### Post by droodlol on 2010-07-21
I have a HP 8510W laptop with similar card where I cant get the mic working (I need it for Skype). The sound output works fine tho.

My lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

My kernel version:
 2.6.29

Sound modules loaded:

snd_hda_codec_analog    58428  1 
snd_hda_intel          25640  0 
snd_hda_codec          68476  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7008  1 snd_hda_codec

What I have tried:

Adding 

options snd-hda-intel model=mitac

or

options snd-hda-intel model=3stack-6ch

to alsa-utils in modprobe.d Also
        amixer set 'Capture' cap

My mic is still muted, any other ideas?:popcorn:

---

### Post by ajgreeny on 2010-07-21
Run ```
alsamixer
``` in terminal.  You may find it is muted in that, or just set at too low a level.

---

### Post by droodlol on 2010-07-21
Of course I checked alsamixer but it doesnt show up

&#9474; Card: HDA Intel                                                                                                                                       &#9474;
&#9474; Chip: Analog Devices AD1981                                                                                                                           &#9474;
&#9474; View: [Playback] Capture  All                                                                                                                         &#9474;
&#9474; Item: Master [dB gain=-52.50, -52.50]       


I can only see a mic boost which is maxed out already.

---

### Post by droodlol on 2010-08-03
So anyone solved it? These HP workstations are more popular than most brands eg asus, fujitsu etc.

---

### Post by TNT1 on 2010-08-04
Hi, it doesn't really help you, but I have used an 8510w running Ubuntu 8.1, and the mic worked, so it must be possible. (I don't have the machine anymore, so I can't check it...)

---

### Post by utilitytrack on 2010-08-04
to** droodlol**

give here 

```
$ lsb_release --all

$ uname -r


$ dpkg -l alsa-*


$ lspci -nn | grep Audio


$ cat /proc/asound/card0/codec#0 | grep Codec


# hwinfo --sound

$ cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by droodlol on 2010-08-05
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

-----

2.6.29

-----
un  alsa                                 <none>                               (no description available)
ii  alsa-base                            1.0.17.dfsg-2ubuntu1                 ALSA driver configuration files
un  alsa-oss                             <none>                               (no description available)
ii  alsa-utils                           1.0.17-0ubuntu3                      ALSA utilities
------

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
-------
Codec: Analog Devices AD1981
------

26: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.310]
  Unique ID: u1Nb.8pi0rMxfR_4
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801H (ICH8 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "82801H (ICH8 Family) HD Audio Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30c5 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xe8044000-0xe8047fff (rw,non-prefetchable)
  IRQ: 30 (812780 events)
  Module Alias: "pci:v00008086d0000284Bsv0000103Csd000030C5bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


And here is a pic about my alsamixer:

[http://yfrog.com/n5hdaintelj](http://yfrog.com/n5hdaintelj)

---

### Post by lidex on 2010-08-06
Try upgrading your alsa install. Use the alsa-upgrade link in my sig.

---

### Post by droodlol on 2010-08-30
Ah man I even tried the latest kernel now, no success.

BTW about your script:

checking for directory with kernel source... Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel

I figured it misses version.h what I made correctly later, still cries with the same error. 
I have custom kernel not ubuntu default.

---

### Post by droodlol on 2010-08-30
I partially solved this by upgrading to Jaunty.

Running kernel is: 2.6.35.4

The microphone in alsamixer still red but with gnome mixer it's possible to adjust the mic level (this itself still doesnt do a thing).

But skype is able to use it finally.
Select the **HDA Intel, AD198x Analog Default Audio Device** from the list in Skype's settings.:popcorn:

---

