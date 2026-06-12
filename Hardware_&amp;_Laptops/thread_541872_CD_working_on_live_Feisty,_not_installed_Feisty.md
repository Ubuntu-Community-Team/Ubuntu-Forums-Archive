---
title: "CD working on live Feisty, not installed Feisty"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Lary Grant on 2007-09-03
I can boot the Feisty CD, but when I boot Feisty from the hard drive, the CD drive no longer works.  Even if I put in the Feisty install CD, I only get "unable to mount" when I try to open it.

I even re-installed Feisty from scratch and installed all the updates, and this problem still persists.

Another piece of info (which I found out by accident!): If I reboot with the Feisty CD still in the drive, I get the Feisty menu asking if I want to boot from the CD, boot from the hard disk, etc.  If I say "boot from the hard disk", I can access my CD drive and see the Feisty CD in there.  But if I eject it, the CD no longer works.  Even if I put back the same Feisty CD, it won't read it.

Any ideas?

---

### Post by Bablefish on 2007-09-03
Not to accuse you of something but did you check your bios after your install? You could of disabled boot from hard drive

---

### Post by Lary Grant on 2007-09-03
It boots fine from the hard drive, but the CD then does not work.

---

### Post by Lary Grant on 2007-09-05
I found this in dmesg, after inserting a CD:

[  362.151898] ata2.00: ATAPI check failed
[  362.151942] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen 
[  362.151950] ata2.00: cmd a0/00:00:00:00:20/00:00:00:00:00/a0 tag 0 cdb 0x0 data 0 
[  362.151952]          res 51/21:03:00:00:20/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
[  362.151979] ata2: soft resetting port 
[  362.645285] ATA: abnormal status 0xD0 on port 0x00010177
[  362.645316] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x2)
[  362.645320] ata2.00: revalidation failed (errno=-5)
[  362.645325] ata2: failed to recover some devices, retrying in 5 secs 
[  374.648730] ata2: port is slow to respond, please be patient (Status 0xd0)
[  397.652675] ata2: port failed to respond (30 secs, Status 0xd0)
[  397.652685] ata2: soft resetting port
[  398.300581] ata2.00 : configured for UDMA/33
[  398.464658] ata2.01: configured for UDMA/66
[  398.464680] ata2: EH complete

---

