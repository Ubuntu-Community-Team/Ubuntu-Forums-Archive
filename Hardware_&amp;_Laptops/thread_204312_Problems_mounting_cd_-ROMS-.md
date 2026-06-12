---
title: "Problems mounting cd -ROMS-"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by CKyle on 2006-06-26
Hello, I've been using Dapper Drake and linux in general for all of one day now, and I have to say things are going smoother than I was expecting. :)

Not all is right, though. I'm having an odd problem with my cdrom. Disk Manager recognizes it as a _NEC DVD+RW ND-5100A located at /dev/hdc, which both seem to be right. (It also puts a red dot next to DVD writing, but I'm not concerned about that right now.)

I've tried and successfully played audio cd's. Also, I put in a movie dvd that was recognized by title in Gxine even though it wouldn't play (I'm thinking maybe codecs still need worked out.) It also recognized a blank cd and I was offered to assistance on burning things.

When I put in a cdrom with files, though, such as the Ubuntu installation CD (which Add/Remove seems to want for network-manager) it won't mount. The drive spins up and beeps a little, but then slows down again only to repeat this several times. Once when I left a CD in for a while I got this in an error box:


```
mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so
```

syslog says:

```
[17180870.132000] hdc: ATAPI reset complete
[17180891.600000] hdc: irq timeout: status=0xd0 { Busy }
[17180891.600000] ide: failed opcode was: unknown
[17180891.840000] hdc: ATAPI reset complete
[17180913.168000] hdc: irq timeout: status=0xd0 { Busy }
[17180913.168000] ide: failed opcode was: unknown
[17180913.408000] hdc: ATAPI reset complete
[17180932.516000] hdc: irq timeout: status=0xd0 { Busy }
[17180932.516000] ide: failed opcode was: unknown
[17180932.756000] hdc: ATAPI reset complete

```

I don't have a problem mounting any other external drives. (These being an iPod and a USB flash drive, both FAT). Does anybody know what may need to be done? I haven't looked too far into NTFS support yet, if that matters, but I don't know why it would for an Ubuntu installation cd. Thanks for any input.

Edit: Oh, and I forgot to mention. When trying to run the Dapper Drake Live CD, it was unable to mount the root. The Breezy Live CD and Dapper Alternate Install worked fine, though.

---

### Post by CKyle on 2006-06-27
Update: I finally got a cdrom to mount, but only after letting it sit in the drive for around 10 minutes. It was the Ubuntu Alternate Install cd and it only stayed mounted long enough for me to get network-manager installed. Almost as soon as the installation completed, the new file manager window for the cd regressed to my home directory. :( I'm assuming the timing was just coincidence, though.

---

### Post by asfpf on 2006-10-12
We have the same problem, even with the same NEC device! I even got another thread opened, but it's the exactly same issue. I couldn't find anything wrong here at all. Let's keep searching... :(

---

### Post by drhoden on 2007-01-06
I'm having trouble with this driver as well.  Hardware manager reports the drive to be:
_NEC DVD+RW ND-5100A

I have a Sam's Club bought HP Pavilion laptop (zd7269cl).  I mention the Sam's Club part because it was a special combo.

I'm running 6.10 Eft.

Some data cd's mount just fine, other I hear it slowly spin up and quickly drop off.  Repeats this several times.  I never let it sit long enough to see if it finally mounted after 10 minutes.

If a cd reads just fine in a different machine (even two), but does that stupid spin up-stop loop on mine, wouldn't that suggest a bad driver?  (assuming the cd reads just fine on the same computer in Windows).

Thanks.

---

