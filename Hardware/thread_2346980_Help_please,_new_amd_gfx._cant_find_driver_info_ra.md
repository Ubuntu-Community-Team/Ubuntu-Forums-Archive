---
title: "Help please, new amd gfx. cant find driver info radeon R4"
date: 2016-12-20
forum: Hardware
---

### Post by neokron2 on 2016-12-20
i have searched high and low, not a total nube. and havent found much of anything on the R4. AMDs website has an R4 driver for download, but its for a desktop. And i just bought a quad core with A-6310 processors. I cannot find the exact specs on the gfx card on any sites. and the camands i run in terminal tell me its an R4, but no specific model.?[ATTACH=CONFIG]272782[/ATTACH][ATTACH=CONFIG]272783[/ATTACH]

link to specs
[http://www.thesource.ca/en-ca/computers-and-tablets/laptops/all-laptops/hp-15-af166ca-15-6%22-laptop-with-amd-a6-6310-apu%2c-500gb-hdd%2c-4gb-ram-and-windows-10-home---turbo-silver/p/108041080](http://www.thesource.ca/en-ca/computers-and-tablets/laptops/all-laptops/hp-15-af166ca-15-6%22-laptop-with-amd-a6-6310-apu%2c-500gb-hdd%2c-4gb-ram-and-windows-10-home---turbo-silver/p/108041080)

and its been a few years.. can i compile a driver for my processors as well? ill google it

---

### Post by Bashing-om on 2016-12-20
neokron2; Hello; Welcome to the forum .

You fail to explain what the issue here is .
Then ->
What release are you running ?
Be aware that there is no proprietary (FGLRX) driver anymore after 14.04.4. AMD has thrown full support to open source.
And no, if you are running 14.04.5+ you can not compile a proper driver anymore either as there is no support for the later x-server version.
Now to the situation at hand:
show us what you are working with:
post back - between code tags - the outputs of terminal commands:
```

lsb_release -a
sudo lshw -C display
lspci -k|grep -iEA5 'vga|3d'
lsmod | grep radeon
lsmod | grep amdgpu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

depending ^
[INDENT][INDENT]is what we do
[/INDENT][/INDENT]

---

### Post by neokron2 on 2016-12-21
Trying to find the best driver setup for my laptop
ubuntu 14.04 64bit
looks like im trying to find out what open souce driver im looking for 
but it would help if i could find the exact driver model
as you can see , it says radeon mullins r4.. but doesnt specify. which is a problem when AMD asks me for a model. which doesnt matter if im going open source.
```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
```
```
~$ sudo lshw -C display
[sudo] password for ghostinaforest: 
  *-display               
       description: VGA compatible controller
       product: Mullins [Radeon R4/R5 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:40 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0d00000-f0d3ffff memory:f0d80000-f0d9ffff
ghostinaforest@GhostInAForest:~$ lspci -k|grep -iEA5 'vga|3d'
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: snd_hda_intel
```
```
$ lspci -k|grep -iEA5 'vga|3d'
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: snd_hda_intel
```
```
$ lspci -k|grep -iEA5 'vga|3d'
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: snd_hda_intel
ghostinaforest@GhostInAForest:~$ lspci -k|grep -iEA5 'vga|3d'
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
    Subsystem: Hewlett-Packard Company Device 80cb
    Kernel driver in use: snd_hda_intel
ghostinaforest@GhostInAForest:~$ lsmod | grep radeon
radeon               1503232  2 
ttm                    94208  1 radeon
drm_kms_helper        143360  1 radeon
drm                   360448  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           16384  1 radeon
```
```
$ lsmod | grep amdgpu
``` gave no response

moving, my apologies for the late reply
and thank you for yours

---

### Post by Bashing-om on 2016-12-22
neokron2; Well ..

Running 'buntu release 14.04.(5) and with the open source driver radeon . All to the good .
Now " Trying to find the best driver setup for my laptop" .. depends on what your use case is .
Many times we find that the open source driver performs the better . Heavy gaming, then we want the proprietary driver.
Now comes the issue with a proprietary driver for AMD/ATI graphics's .
AMD has thrown full support to open source; and depending on what kernel you are running in 14.04.5 is what our options are.
Please post back:
```

uname -r

```
Then we can further discuss what you want to do.

[INDENT][INDENT]it's open source
[INDENT][INDENT][INDENT]all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2016-12-24
> the commands i run in terminal tell me its an R4, but no specific model.

That IS the complete marketing name/model. To date, the R4 series only has one GPU in it, so there are no additional model numbers in the name like parts in the R7 family (for example).

---

