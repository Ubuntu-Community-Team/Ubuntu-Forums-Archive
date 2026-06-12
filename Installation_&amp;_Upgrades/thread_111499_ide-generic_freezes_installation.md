---
title: "ide-generic freezes installation"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by peco on 2006-01-02
Dear All,
            before posting here I had a long look around to find if anyone have had the same problem but it seems noone.

I try to do the net installation since it's not possible to use the CD. I use grub configured with this parameters:

title  New Install
kernel (hd0,6)/boot/linux root=/dev/ram0 ramdisk_size=33000
initrd (hd0,6)/boot/initrd.gz

It seems the installation starts properly but the system freezes when it gets to hardware detection and in particular the drive ide-generic.ko.

I've alreday installed Ubuntu on my laptop without problems.

This is my system in brief:
mobo Asus A7V
cpu Athlon Thunderbird 800MHz
Ram 256Mb
HD: Maxtor 6 Y080L0 SCSI Disk Device 80Gb (master) + QUANTUM FIREBALLP LM SCSI 14Gb (slave)
DVD-WR _NEC DVD_RW ND-2510A SCSI CdRom Device (master)
CD-ROM CREATIVE CD5233E SCSI CdRom Device (slave)
HD+DVD+CD on UDMA100 busses

I've already tried with different parameters: noapic, nolapic, acpi=off, pci=biosirq e irqpoll.

Furthermore I've tried with bios loaded in shadow and not.

Thanks in advance for any suggestion.

Regards

---

