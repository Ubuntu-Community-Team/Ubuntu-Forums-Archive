---
title: "Getting raids to work"
date: 2010-07-17
forum: Hardware
---

### Post by garnie on 2010-07-17
Hello

I just recently installed Ubuntu on my stationary PC where I'm also running windows 7 in a dual boot environment

In windows 7 i have 2 raids consisting of the following:

2 x 1,5 TB discs
2 x 400 GB discs

I now want to be able to read these in linux, not sure if I'm able to write to them, though that is not important either.

Its just i have no idea where to start, i have gotten mdadm and dmraid installed and "dmraid -r" returns the following

```
rasmus@rasmus-desktop:~$ sudo dmraid -r
no raid disks
```

which have left me a little clueless on what i should do next because I'm not really 100% sure what I'm doing and i don&#836;'t want to delete it all by accident. 

Any help will be appreciated

---

### Post by ronparent on 2010-07-17
For accessing raids created in windows, dmraid is your only choice. The command dmraid -r will not endanger your raid setup. What is your raid chipset? Also it would be safe to run dmraid -l to see if your raid chipset is supported.

---

### Post by garnie on 2010-07-18
Sorry about the late reply got sidetracked with some networking issues which are not resolved yet, damn r8168 driver :(.

Anyway ..

i took at look at lspci:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.3 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation Device 06c4 (rev a3)
01:00.1 Audio device: nVidia Corporation Device 0be5 (rev a1)
02:00.0 IDE interface: Device 1b4b:91a3 (rev 11)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
05:05.0 IDE interface: Integrated Technology Express, Inc. IT8213 IDE Controller
```

and the dmraid -l
```

asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs
```

And to me it seems that my controllers are'nt supported which i guess is just bad luck with nothing i can do then ?

---

### Post by ronparent on 2010-07-18
You haven't said what your raid chipset is, but, if it isn't listed above then it isn't supported. There is nothing you can do short of an unlikely possibility that the manufacturer supplies a linux driver.

---

### Post by garnie on 2010-07-25
Sorry about the very late replay, have been busy banging my head with network problems.

On my motherboard there is 2 intel and 1 marvel sata chipset and all discs are connected to the intel chipsets, so they should be supported yes ?

---

