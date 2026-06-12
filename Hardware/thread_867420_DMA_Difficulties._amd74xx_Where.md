---
title: "DMA Difficulties. amd74xx??? Where?"
date: 2008-07-22
forum: Hardware
---

### Post by Monster_user on 2008-07-22
I just upgraded to Hardy Heron, from Gutsy Gibbon, and I seem to have lost the DMA support for my computer.

The result is nearly unbearably slow performance at times. 

I have an older model nForce motherboard, with an AMD Athlon XP processor. 
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

I read the support page, and the amd74xx module does not even appear on my system.

---

### Post by Monster_user on 2008-08-14
Well, I have not found any of the bug reports. None HD related. Can anybody confirm or deny the existence of the amd74xx module in a 2.6.24 kernel?

I have managed to compile this troubleshooting list, from reading a Usenet thread.

> Troubleshooting Hard Drives & DMA...

Enable DMA.
 -> hdparm -d1 /dev/hda

Check Loaded drivers 
 -> lspci -nn
 -> dmesg | grep grep -Ei 'ata|ide|amd74xx|pata_amd|ata_piix'
 
Check installed drivers
 -> cd /lib/modules/<kernel version>/kernel/drivers/ide/pci
 -> ls

Check Driver used
 -> udevadm info -a --name /dev/hda

----

<Dangerous>
 - boot with "blacklist=ide_generic" appended to the kernel command line

Module Config Files
 -> "/etc/initramfs-tools/modules"
Update
 -> initramfs-tools -k $(uname -r) -u
</Dangerous>


[Source](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-07/msg01471.html)

My lspci -nn output.

> 00:00.0 Host bridge [0600]: nVidia Corporation nForce CPU bridge [10de:01a4] (rev b2)
00:00.1 RAM memory [0500]: nVidia Corporation nForce 220/420 Memory Controller [10de:01ac] (rev b2)
00:00.2 RAM memory [0500]: nVidia Corporation nForce 220/420 Memory Controller [10de:01ad] (rev b2)
00:00.3 RAM memory [0500]: nVidia Corporation Unknown device [10de:01aa] (rev b2)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce ISA Bridge [10de:01b2] (rev c3)
00:01.1 SMBus [0c05]: nVidia Corporation nForce PCI System Management [10de:01b4] (rev c1)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce Audio [10de:01b1] (rev c2)
00:06.1 Modem [0703]: nVidia Corporation nForce AC'97 Modem Controller [10de:01c1] (rev c1)
00:08.0 PCI bridge [0604]: nVidia Corporation nForce PCI-to-PCI bridge [10de:01b8] (rev c2)
00:09.0 IDE interface [0101]: nVidia Corporation nForce IDE [10de:01bc] (rev c3)
00:1e.0 PCI bridge [0604]: nVidia Corporation nForce AGP to PCI Bridge [10de:01b7] (rev b2)
01:09.0 FireWire (IEEE 1394) [0c00]: NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr [1033:00f2] (rev 01)
01:0a.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
01:0a.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
01:0a.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)
01:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:00.0 VGA compatible controller [0300]: nVidia Corporation NV40 [GeForce 6800] [10de:0041] (rev a1)

"udevadm info -a --name /dev/hda" Output.

> Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/hda':
    KERNEL=="hda"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{dev}=="3:0"
    ATTR{range}=="64"
    ATTR{removable}=="0"
    ATTR{size}=="312581808"
    ATTR{stat}=="  409966  1743685  8428347  6616892  8128002  3951695 96643561 275527088        1 88414720 282127680"
    ATTR{capability}=="10"

  looking at parent device '/devices/ide0/0.0':
    KERNELS=="0.0"
    SUBSYSTEMS=="ide"
    DRIVERS=="ide-disk"
    ATTRS{media}=="disk"
    ATTRS{drivename}=="hda"
    ATTRS{modalias}=="ide:m-disk"
    ATTRS{model}=="WDC WD1600JB-00GVA0"
    ATTRS{firmware}=="08.02D08WDC WD1600JB-00GVA0"

  looking at parent device '/devices/ide0':
    KERNELS=="ide0"
    SUBSYSTEMS==""
    DRIVERS==""

Once again, can anybody confirm, or deny the existence of the amd74xx module in the 2.6.24, or a future 2.6.25 kernel?

Or confirm, or deny that this chipset is compatible with the pata_amd module?

---

