---
title: "Combination of SATA and IDE drives?"
date: 2011-10-18
forum: Hardware
---

### Post by A Traveller on 2011-10-18
Hi All.

I would like to have a SATA drive as the main drive that the pc boots into automatically. The motherboard ([http://www.gigabyte.com/products/product-page.aspx?pid=3516#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3516#sp)) allows up to two IDE devices. I would like to have either two IDE drives (dual boot or for storage) or an IDE drive and an IDE CD/DVD ROM drive.

I did an Internet search just to confirm that this was a simple, straightforward process, however, came across all sorts of reported issues and complicated instructions.

Before I try anything, is there anything else I need to do apart from connect the right cables to the right sockets? Do I still need to set the jumpers of first IDE drive as the master and the second IDE drive or CD/DVD ROM drive as the slave? Do I need to make any changes in BIOS?

Thanks for any advice.

---

### Post by SeijiSensei on 2011-10-18
> **A Traveller said:**
> Before I try anything, is there anything else I need to do apart from connect the right cables to the right sockets? Do I still need to set the jumpers of first IDE drive as the master and the second IDE drive or CD/DVD ROM drive as the slave? Do I need to make any changes in BIOS?


Yes, you'll still need to set the jumpers.  Most factory-built systems that had both a CDROM and a hard drive on the same cable made the CDROM the primary.  I recall having at least one machine where setting them with the hard drive as the primary caused the CDROM to fail.

If you have a CDROM and a hard drive, make the CDROM the master and plug the connector on the end of the IDE ribbon cable into it.  Make the hard drive the slave and plug into it the socket connector in the middle of the ribbon cable.

Once the drives are installed, boot, then enter the BIOS setup screen as directed (usually you press an "F" function key or Del).  You should have a menu entry that lists the hard drives.  Make sure they're all visible.  If you only had the SATA drive in this machine before, you may have had to turn off the IDE controller to avoid getting complaints from the BIOS during boot. If you don't see the IDE drives, make sure their controller is set to On or, better, Auto.  You will need to reboot after changing this setting to force the BIOS to detect the drives.

If the BIOS lets you designate a default boot device, make sure it points first to the CDROM then next to the SATA drive.

Now reboot and check that the BIOS reports all the drives.  (If your BIOS displays a "splash screen," turn that off in the BIOS settings before rebooting.)  If /dev/sda already has a bootable operating system on it, it should boot once more.

**Edit**:  I looked at the motherboard; you apparently only have a single IDE connector.  I'd go with a SATA optical disk and use the IDE connector to support two hard drives.  Alternatively you can buy a cheap four-port IDE board like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115016"); it also provides hardware RAID 0/1/5/10.

---

### Post by oldfred on 2011-10-18
Check what options BIOS has.

If you are using cable select be sure to use a 80 conductor cable, most CD drives only have the 40 conductor cable.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

Some BIOS automatically promote the IDE drive to sda. Some drives do not come up at same time and then the sda/sdb will not always be the same. That is part of the reason Ubuntu uses UUID so device order is less important.

---

### Post by A Traveller on 2011-10-19
Thanks for your replies SeijiSensei/oldfred.

I've never had a SATA drive in the PC, just IDE, so that probably means that the IDE controllers are on (or auto). Yes the motherboard only has a single IDE connector but two devices can be connected to it via one cable. At the moment, it'll have to be the SATA as the main drive and the additional drives and CD-ROM to be IDE.

I have current IDE cables as the motherboard came with one.

Thanks for the info/advice. I'll try it and see how it goes.

---

### Post by A Traveller on 2011-10-25
Hi all.

Well I tried it and it all worked perfectly! Thanks all.

---

