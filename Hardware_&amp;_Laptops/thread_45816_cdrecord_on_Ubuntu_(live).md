---
title: "cdrecord on Ubuntu (live)"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by Tux on 2005-07-01
Hi:
I am in urgent need to salvage data from a hard disk and burn it onto CD.  I have been trying to use the Ubuntu live CD as a rescue CD, but I cannot get it to write to my CD-R.

This is the situation:

I used to have a Debian installation on 2 IDE HD's.  One, which contained most of the system (/usr etc.), broke down.  I managed to create an ISO image of some data onto the 2nd "good" disk, but the system broke completely before I could cdrecord it.
I threw out the bad disk and the good disk is now my /dev/hda ; however I cannot boot from it, so I am trying live CD's.

I have 2 CD's on a second IDE controller:
* /dev/hdc is an ordinary CD from which I can boot the Ubuntu live CD. 
* /dev/hdd is my CD-R.

I can mount the relevant partition from hda where my iso image is.  However when I try to burn it with the Nautilus CD/DVD Creator it does not recognise the empty media.  If I put a written CD into the CD-R, Nautilus comes up automatically with a media icon - so in principle the decive is useable.

If I run cdrecord (e.g. cdrecord -scanbus) it complains about 2 things:
1) kernel 2.6 (which Ubuntu uses) would give problems with cdrecord
2) it cannot find /dev/sg*
Indeed there are no /dev/sg* and I wouldn't know why cdrecord goes look for them.
The way things used to work is that writeable CD's are approached through the SCSI emulator.  The scsi_mod and ide_scsi modules are both loaded.
I used to boot my kernel with boot parameters for this purpose.  I tried to boot Ubuntu the same way, as follows:
boot: live hdc=ide-cd hdd=ide-scsi
This still does not make cdrecord or the CD/DVD creator recognise the CD-R.

Any advice?

---

### Post by Tux on 2005-07-01
Follow-up on myself:
OK, `cdrecord -scanbus` couldn't recognise any pseudo-scsi devices, but after some systematic trying the option "dev=ATA:1,1,0" (i.e. 2nd ATA controller, 2nd (=slave) device, 1st LUN) made things work.  Although it is an ATAPI device, " ATAPI:" didn't work.
I got my data on CD so I'll wipe the disk and install Ubuntu anew.

One question remains: how do I tell cd CD/DVD Creator to approach the appropriate ATA device and not go look for the non-existing /dev/sg* or /dev/pg* ?

---

