---
title: "Sil3114 Sata Controller installation"
date: 2008-09-10
forum: Hardware
---

### Post by AnarkistNZ on 2008-09-10
Hi everyone.

I've been using Linux for about 18 months or so now, and am generally confident doing most things now. I'm at a bit of a brick wall however with how to install hardware as I've never had to do it before.

I have a new Sil3114 Sata Controller (an STLab A-224) that I want to run a few SATA disks off as I've used the 2 onboard SATA ports already.

Here is the output of lspci

```

root@farpho:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:07.0 RAID bus controller: Imagenation Corporation Unknown device 3114 (rev 02)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```

Once I've plugged the hardware in, where is the best place to start with it? I'm running Ubuntu Server 8.04.

fdisk -l doesn't show the devices being detected so I figure I need to configure the SATA controller some how.

Any pointers on where to start are much appreciated. Thanks :)

---

### Post by CityofAsh on 2008-09-10
did you run 
```
sudo fdisk -l
```
That command wont see anything unless you are root. The sata disks you installed are they partitioned?

I just installed a PCI SATA IDE Controller today and 1 200 gb sata disk. All worked fine.

---

### Post by AnarkistNZ on 2008-09-10
> **CityofAsh said:**
> did you run 
```
sudo fdisk -l
```
That command wont see anything unless you are root. The sata disks you installed are they partitioned?

I just installed a PCI SATA IDE Controller today and 1 200 gb sata disk. All worked fine.

Yeah, I ran fdisk as root.

The disks are non-partitioned. Brand new disks that will be configured as a RAID 1 array and formatted after that. However they should be shown in fdisk whether they're formatted or not however.

I've looked around and it seems the drives should be listed under /dev/mapper/ but that directory doesn't exist.

I wasn't sure whether I needed to add the sil_sata module to the kernel or anything, I really have no idea where to start when it comes to installing hardware.

*shrug*

---

### Post by CityofAsh on 2008-09-11
Did you find/read this documentation?

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

Looks like what you are trying to do. I have never installed a raid array.

Good luck.

---

### Post by AnarkistNZ on 2008-09-11
Thanks, I understand the process for creating a RAID array (I already have a functional RAID1 array configured in that box)

I'm not sure how to install a SATA controller, and need some pointers on that.

At this stage it looks as if I need to add sata_sil to /etc/modules or build a custom kernel with support for that module. I'm unsure though, hopefully anyone can shed some light on it.

---

### Post by CityofAsh on 2008-09-12
Ah. Well it should be a CRTL + F6 or something on boot. Then you should be in the controllers bios. And make sure its set on SATA. 

The controller i installed just works ad an IDE/SATA controller. Not raid. I just plugged it in with the SATA HDD and it worked fine.

Sorry i cant help.
Good luck m8!

---

### Post by IntuitiveNipple on 2008-09-12
This would seem to be the device but you need to use additional lspci options to show the vendor and device ID:
```

00:07.0 RAID bus controller: Imagenation Corporation Unknown device 3114 (rev 02)

```
Try this:
```

lspci -nn

```
From the vendor/product ID combination you can search the kernel's ID list to find out which, if any, driver supports that hardware. If it is new it is possible there isn't driver support in the current kernel, although it may be in the Linux mainline for 2.6.26/27.
```

# set the actual device IDs here:
# vendor ID
VID="0000"
# product ID
PID="0000"
egrep '0x0000${VID}.*0x0000${PID}' /lib/modules/$(uname -r)/modules.pcimap

```

---

