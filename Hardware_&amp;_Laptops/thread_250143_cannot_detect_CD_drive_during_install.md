---
title: "cannot detect CD drive during install"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by jjen009 on 2006-09-03
I am trying to install ubuntu.  I can boot fine off my CD drive but then at the beginning the install it says it cannot find the CD drive.  It suggests the CD may not be in the drive but of course it is.  I have actually tried putting a different drive into the machine with the same results.  An older (766MHz) Dell Tower with two SCSI drives (no IDE) drive.  The CD is on IDE0 as Master.

---

### Post by mssever on 2006-09-03
It's possible that the CD itself is bad. You might try another CD (another burn, or even another download--be sure to check the md5sum).

---

### Post by jjen009 on 2006-09-03
I have tried that CD on another machine, did the test-CD on it and it's fine.  I have run the memory test off it on the target machine for hours and it's fine.  Actually, I also tried a kubuntu CD on the target machine - same issue.  That was when I decided to try ubuntu.  As I said, it boots fine from the CD.  When I try the test-CD on the target machine, it also says there is nothing in the CD drive

---

### Post by Omnios on 2006-09-03
How many cd-roms do you have and could the biosy be set to another one?

---

### Post by jjen009 on 2006-09-03
Only one CD drive, and, no, the BIOS is fine.  Remember, it can boot from the CD drive, just when it subsequently looks for it to install from it, or to test from it, it says there is no CD in the drive.  BTW I have tried setting the drive to slave instead of master; same deal.

---

### Post by jjen009 on 2006-09-03
I should say that I really don't think there is anything wrong with the machine.  I have had both Windows and Debian (two versions) installed in the past with no difficulty.  And everything works fine up until you say 'go ahead and install.'  Then it runs something that says it is detecting hardware and trying to find the CD drive (which is odd since it already booted from it).  Then it says it can't find it and the likeliest reason is that there is no CD in the drive.  It's an ordinary Dell tower, Dell Dimension, I believe, although I am not physically near the machine at present to see.

---

### Post by jjen009 on 2006-09-03
PS - ordinary Dell except, of course, for the SCSI controller.  But I had Debian working on it before with that controller.

---

### Post by jjen009 on 2006-09-04
Hmm.  So far not much concrete help.  here are the grotty details in case anyone is able to help.

Machine is a Dell Dimension B733r (not 766 as I thought) with 256MB RAM

I have tried ubuntu alternate now, too.  All forms get to the point of saying:

Detecting hardware to find CD-ROM drives
Detecting hardware, please wait...

Then:

process:pidnumber-whatver): mount:
process:same number: mounting /dev/cdroms/cdrom0 on /cdrom failed
process:pid: Invalid argument

Then it gives you two choices:

<Yes> to retry
<No> not to retry

Whichever you choose, it just retries.  The only way out is to reboot.  Note that I am booting from the CD itself so it can certainly read it, and I have run the cd-check on another machine.

---

### Post by tenjin1 on 2007-09-13
worth a try: eject the disk when u see that error and load it again to get the drive to re-read.

---

