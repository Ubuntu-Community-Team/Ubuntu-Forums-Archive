---
title: "Raid 0 failing, any way to backup individual hdd?"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by hapveg on 2007-12-17
My question first, then the background information:
Is it possible to copy the data from a failing drive onto a spare drive, and replace it in a raid 0 without any problems?

Possibly relevant background:
One of the hard drives in my raid 0 is failing, it sometimes wont start up properly, and randomly has very loud seeks.

The first thing I did was backup my important data to another drive, but now I'm wondering if there is a way to fix this problem.

The raid 0 is 4*160gb Samsung Spinpoint SATA drives, I have a spare drive (160gb spinpoint, but purchased about 6 months later).

The raid is software, done by my P5B Deluxe motherboard (ICH8R, 6 sata ports, but only 4 support raid).

The raid is my Windows XP drive (bootable), but I've other hard drives with WinXP and Ubuntu, so I'll try any tool recommended.

Any help very much appreciated.

---

### Post by crouton on 2007-12-17
This doesn't really fall under Ubuntu support as the RAID is done by the motherboard.  However, in general, RAID0 won't support a drive-swap like you are asking about, as you are striping data across all 4 disks.  By nature striping increases the likelihood of failure (just 1 of 4 means you're toast) so you need to plan accordingly, either by having a consistent backup schedule or some other means of recovery.

There is one potential way to accomplish this task you seek, but I will warn you that you should already be preparing yourself for data loss and/or complete system reinstall.  NOTE!  Unless you have another computer with SATA ports, you may completely bork the RAID array by simply pulling drives out and/or putting them back in the wrong order.  Like I said, be prepared for total data loss.


That said, you can attempt to do a bit-level drive copy.  A program called 'ranish' on the SysRescCD (google for it) will do this.  You will need to put the bad drive and your spare drive in the same system, boot the CD, run the program when prompted, and tell it to copy the entire drive (option is 'd' I believe) from the bad to the spare.  These drives need to be separate from the RAID array, so you might get lucky putting them on ports 5 and 6, but again you're playing with complete data loss if something goes wrong.


With any luck, you didn't blow away your RAID array, the drive copy was successful, and you're back on your feet with a happy RAID0.  Consider a safer RAID array unless you absolutely need all that space in one drive.

---

