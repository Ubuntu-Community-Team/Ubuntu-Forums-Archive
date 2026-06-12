---
title: "DVD - DriveReady SeekComplete Error"
date: 2004-10-26
forum: Hardware &amp; Laptops
---

### Post by chombee on 2004-10-26
I installed Ubuntu on my Dell Latitude Cpx laptop which has a DVD-rom,
the DVD drive doesn't work (in Ubuntu, but the drive itself is not
broken because I used it to install Ubuntu in the first place) and I
don't really know what to do about it.

When I go to `Disks' in the `Computer' menu and click the `CD Rom 1'
link I get:

Unable to mount the volume. There is probably no media in the device.

There isn't a link for a DVD Rom in there, I looked around a bit and I
can't find it mounted anywhere in /dev/ or /media/ or /mount/.

I scanned the mailing lists etc and tried some things in the command
line that other people had used, for example:

# ls -l /dev/ | grep cdrom
lrwxrwxrwx    1 root     root            3 2004-10-26 11:56 cdrom ->
hdc
brw-rw----    1 root     cdrom     22,   0 2004-10-26 11:56 hdc

And, one that seems particularly revealing:

# dmesg|grep ^hd
hda: IBM-DARA-218000, ATA DISK drive
hda: max request size: 128KiB
hda: 35433216 sectors (18141 MB) w/418KiB Cache, CHS=35152/16/63,
UDMA(33)
hdc: TOSHIBA DVD-ROM SD-C2612, ATAPI CD/DVD-ROM drive
hdc: ATAPI 24X DVD-ROM drive, 192kB Cache, UDMA(33)
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error
}
hdc: packet command error: error=0x50
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error
}
hdc: packet command error: error=0x50
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error
}
hdc: packet command error: error=0x50
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error
}
hdc: packet command error: error=0x50
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error
}
hdc: packet command error: error=0x50

I don't know how to deal with this, any clues?

Thanks,
Sean

---

### Post by jdong on 2004-10-26
those errors typically indicate damaged media. Have you tried lots of different CD's?

---

### Post by chombee on 2004-10-27
Yeah i've tried lots, including the Ubuntu cd which I used to install the system, with the same drive

---

### Post by chombee on 2004-10-27
I think the problem is driver/kernel module related. Lots of messages
scroll past when I boot the laptop, of course too fast for me to
read. But some of them complain in various ways that the following
modules could not be loaded:

shpchp
pciehp
toshiba-acpi

The last one in particular looks like it could explain the
non-functioning DVD drive. However, I don't really know what I'm
doing.

---

### Post by chombee on 2004-10-27
Okay, I'm coming to the conclusion that the drive is broken, which I think the SeekComplete error suggests - a hardware fault. Ubuntu certainly seems to have detected the drive as you can see from the output of my commands earlier, but then runs into this error whenever I try to use it.

Though I booted from the drive to install Linux, when I tested it by trying to boot from the drive again it worked once out of about 10 attempts.

I'm just concerned over one particular message I got out of linux;

failed to load module toshiba_acpi

at boot. Perhaps someone can put my mind to rest and help confirm it's a broken drive - could this message occur BECAUSE of a hardware fault? Or is it more likely that the problem is because of this message?

---

### Post by jdong on 2004-10-28
[QUOTE=chombee]Okay, I'm coming to the conclusion that the drive is broken, which I think the SeekComplete error suggests - a hardware fault. Ubuntu certainly seems to have detected the drive as you can see from the output of my commands earlier, but then runs into this error whenever I try to use it.

Though I booted from the drive to install Linux, when I tested it by trying to boot from the drive again it worked once out of about 10 attempts.

I'm just concerned over one particular message I got out of linux;

failed to load module toshiba_acpi

at boot. Perhaps someone can put my mind to rest and help confirm it's a broken drive - could this message occur BECAUSE of a hardware fault? Or is it more likely that the problem is because of this message?[/QUOTE]


Toshiba laptops have special extensions to their power management (ACPI) drivers, in order for them to work properly under Linux and not fry themselves.

The Hotplug detection routine "thought" that your system needed these Toshiba drivers. When it loaded the drivers, the driver couldn't find Toshiba hardware, and thus refused to stay active. It's perfectly normal.

Same explanation for the ****hp drivers. Those are hotplug drivers... If you can't rip PCI cards out of your box while it's turned on, you don't have PCI hotpug  :grin:


In short, these errors have **no connection whatsoever** to a broken drive.

---

### Post by ispmarin on 2006-04-19
Getting the same errors when trying to mount a dvd drive and a cd drive:
dmesg:
[14680.657417] cdrom: hda: mrw address space DMA selected
[14680.718726] cdrom: hda: mrw address space DMA selected
[14680.740258] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[14680.740265] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[14680.740269] ide: failed opcode was: unknown
[14680.740272] end_request: I/O error, dev hda, sector 64
[14680.740955] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
The drive was working on another computer (Pentium 4 with Asus), but now is complaining on my amd64 with Asus. Any ideas?

---

### Post by phunkizm on 2006-10-11
> **jdong said:**
> Toshiba laptops have special extensions to their power management (ACPI) drivers, in order for them to work properly under Linux and not fry themselves.

The Hotplug detection routine "thought" that your system needed these Toshiba drivers. When it loaded the drivers, the driver couldn't find Toshiba hardware, and thus refused to stay active. It's perfectly normal.

Same explanation for the ****hp drivers. Those are hotplug drivers... If you can't rip PCI cards out of your box while it's turned on, you don't have PCI hotpug  :grin:


In short, these errors have **no connection whatsoever** to a broken drive.

I have the same problem (i believe), but with the hp drivers.  Is there a solution to this?  I've done some searching, and it doesn't seem to be a problem very many people have. 
... or perhaps I'm just not a good googler. :-?

---

### Post by Anubis on 2007-11-19
hda: command error: status=0x51 { DriveReady SeekComplete Error }

Getting those errors , as well as these:

[   30.241431] ide: failed opcode was: unknown
[   31.866496] ide: failed opcode was: unknown
[   39.188838] ide: failed opcode was: unknown

I thought it was the drive I just removed that was connected tog a 40 pin cable going bad. I don't think so now. I think the 40 pin cable was keeping sound-juicer and serpentine from working correctly. But to see these errors again with a good drive, are troubling. At least SJ and Serpentine are working now.

---

