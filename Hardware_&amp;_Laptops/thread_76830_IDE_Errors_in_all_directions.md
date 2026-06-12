---
title: "IDE Errors in all directions"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by Pathogenix on 2005-10-15
Evening, all.
I recently made a bit of a mess of my primary master, had to reinstall Windows, all good clean fun, etc. etc.

Windows is fine. Ubuntu is fine.

However, on booting, I get the following messages which go on for ... oh, days if I let them.


```
Oct 15 11:14:38 localhost kernel: Capability LSM initialized
Oct 15 11:14:38 localhost kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
Oct 15 11:14:38 localhost kernel: cdrom: hdd: mrw address space DMA selected
Oct 15 11:14:38 localhost kernel: hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 15 11:14:38 localhost kernel: hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=65670918, sector=65670894
Oct 15 11:14:38 localhost kernel: ide: failed opcode was: unknown
Oct 15 11:14:38 localhost kernel: end_request: I/O error, dev hda, sector 65670894
Oct 15 11:14:38 localhost kernel: Buffer I/O error on device dm-2, logical block 6588
Oct 15 11:14:38 localhost kernel: hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 15 11:14:38 localhost kernel: hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=65670918, sector=65670896

```

The thing that really perplexes me is that the errors occur on different logical blocks every time I boot. 

hda is the windows drive, partitioned into three, only one of which is mounted under Ubuntu and all three partitions seem to be working quite happily.

I suppose I can stick a line into fstab to ignore the errors, but that feels a little like building a skyscraper on a fault line.

Can anyone shed any light on this, or at least tell me where I can start looking?

---

### Post by hachre on 2005-10-15
I'm having similar errors to these when I try to install 5.10.
They occur on my CD-Rom drive.

What Mainboard and Chipset do you have?

I have a MSI Mainboard Neo2 Platinum with NForce 3 Chipset...

The CD is triple checked - it's fine. I guess the NVIDIA IDE Driver doesn't really work or something... However I can't install Ubuntu :(

5.04 works btw and still does.

---

### Post by Pathogenix on 2005-10-16
Mainboard is some obscure Taiwanese contraption made of semi-conducting blu-tack and bits of string, the graphics card is a GeForce 4.

What makes you think it's an NVidia problem, just out of curiosity? I'd have immediately thought it was a hard drive issue.

My problem manifested after I ran amok with ntfsresize, Breezy has installed quite happily despite the errors.

---

### Post by hachre on 2005-10-16
My harddrivers are on another controler. The problem I have is it can't read the cdrom correctly. The cdrom however works perfectly for Hoary. So it must be the IDE driver -> onboard NVIDIA IDE Controler ....

---

### Post by hachre on 2005-10-16
I was asking about your chipset btw not your graphics card :)

---

### Post by Pathogenix on 2005-10-16
Good point, that man - hardware is something I leave to other people :) If I could run software without resorting to ugly grey boxen I'd be a happy coder.

Chipset is VIA Rhine. I think something's gone wrong when partitioning, and Windows is looking the other way. I'll run chkdsk and see what occurs.

---

