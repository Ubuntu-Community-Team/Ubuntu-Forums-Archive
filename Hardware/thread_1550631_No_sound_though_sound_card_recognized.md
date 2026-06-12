---
title: "No sound though sound card recognized"
date: 2010-08-11
forum: Hardware
---

### Post by Favilla on 2010-08-11
No sound though sound card recognized

Hello. I am new to Linux and Ubuntu.
I just installed Lucid on my laptop, which is a VAIO VPCEA28EC. But the problem came that no sound came out. I checked the volume control, and it's not muted.
So I tried the comprehensive sound problem solutions guide from this forum, but still can't figure out what is wrong.

I tried "aplay -l", and got the following playback:

card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  subdevice: 1/1
  subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  subdevice: 1/1
  subdevice #0: subdevice #0

I guess this means that the sound card is installed. I went to alsamixer and made sure every channel was unmuted.(actually turned them all up to 100.)
Then "sudo alsactl store 0". Rebooted after that.
Still, no sound came out.

I am sure alsa is updated.

I tried "lapci -v", and found

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f5e00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
and

01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
    Subsystem: Sony Corporation Device 9071
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0040000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

And I had my username in the /etc/group.

I don't know what to do next. Does anyone have an idea?

---

### Post by utilitytrack on 2010-08-11
Hello, Put on forum more diagnostics info. 
```

$ uname -r
$ dpkg -l alsa-*
$ lspci -nn | grep Audio
$ head -n 1 /proc/asound/card*/codec#*
$ cat /etc/modprobe.d/alsa-base.conf | grep options
# hwinfo --sound

```

Also recheck levels in[FONT="Courier New"] alsamixer[/FONT]

---

### Post by Favilla on 2010-08-14
I did what you said, and got these results(from which I couldn't figure out anything wrong, or rather, in which I couldn't really fully understand anything.) Still long way to go before I get used to Linux(and be skillful).

"uname -r":
2.6.32-24-generic

"dpkg -l alsa-*":
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name         Version         Introduction
+++-==============-==============-===========================================
ii  alsa-base      1.0.22.1+dfsg- ALSA driver configuration files
un  alsa-oss       <None>          (No related introduction)
ii  alsa-utils     1.0.22-0ubuntu ALSA utilities

"lspci -nn | grep Audio":
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]

"head -n 1 /proc/asound/card*/codec#*":
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

"cat /etc/modprobe.d/alsa-base.conf | grep options":
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-pcsp index=-2

Then I tried "hwinfo --sound", but it's not installed.
So I installed hwinfo and libhd16, then
"hwinfo --sound":
11: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3b56
  Unique ID: u1Nb.T0oPb8X5d04
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel Ibex Peak High Definition Audio"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3b56 "Ibex Peak High Definition Audio"
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x9071 
  Revision: 0x05
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf5e00000-0xf5e03fff (rw,non-prefetchable)
  IRQ: 22 (1187 events)
  Module Alias: "pci:v00008086d00003B56sv0000104Dsd00009071bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 100.1: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_aa60
  Unique ID: NXNs.LiIlsUBLqAD
  Parent ID: vSkL.v_+I6xiKU82
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "ATI Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaa60 
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x9071 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf0040000-0xf0043fff (rw,non-prefetchable)
  IRQ: 17 (217 events)
  Module Alias: "pci:v00001002d0000AA60sv0000104Dsd00009071bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (PCI bridge)

I rechecked AlsaMixer and I am sure all channels are up to 100 except <Headphone> and <Mono>. These two don't have bars to change their levels.

---

### Post by aircooledbusnut on 2010-08-30
I have the same issue -- Sony Vaio - VPCEA24FM

uname -r
2.6.32-24-generic

dpkg -l alsa-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                               Description
+++-=====================================-=====================================-==========================================================================================
ii  
alsa-base                             1.0.22.1+dfsg-0ubuntu3                ALSA driver configuration files
un  
alsa-oss                              <none>                                (no description available)
ii  
alsa-tools                            1.0.22-0ubuntu1                       Console based ALSA utilities for specific hardware
ii  alsa-utils   

lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

 cat /etc/modprobe.d/alsa-base.conf | grep options
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-pcsp index=-2

  hwinfo --sound

12: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_3b56
  Unique ID: u1Nb.T0oPb8X5d04
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel Ibex Peak High Definition Audio"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x3b56 "Ibex Peak High Definition Audio"
  SubVendor: pci 0x104d "Sony Corporation"
  SubDevice: pci 0x9071 
  Revision: 0x05
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf6000000-0xf6003fff (rw,non-prefetchable)
  IRQ: 22 (918 events)
  Module Alias: "pci:v00008086d00003B56sv0000104Dsd00009071bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


Alsa mixer levels all at 100 (max)

Thanks

---

### Post by aircooledbusnut on 2010-08-30
update:

Used a C-Media USB audio dongle.  I have sound through it but not speakers, or headset jack.

My other issues, i.e. USB devies not enumerated.  may be the ultimate cause, as I have no webcam or mic either.

????Does sony power their speakers through the USB hub.?????

Update: Solved USB problem by removing all power incl. battery for thirty minutes.  Everything works except the speakers and jacks on the front.  Still have sound through the CMedia external usb adapter.

---

### Post by aircooledbusnut on 2010-09-09
this how to fixed my sound problem.

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

