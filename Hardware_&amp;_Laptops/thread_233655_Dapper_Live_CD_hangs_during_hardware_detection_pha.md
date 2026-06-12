---
title: "Dapper Live CD hangs during hardware detection phase of install"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by gtmaneki on 2006-08-10
Hi.  I'm returning to Linux after a few years of hiatus, and am excited to see what has happened in my absence.  I want to try out Dapper (Kubuntu version), but the hardware detection phase during install hangs.  I let it run for 2 hours last night and the progress bar stayed at 0%.  I am hoping someone out here can help me.

Here are the specs of my computer:
Athalon 1.3 GHz
512 MB RAM

Disk drives (all IDE/ATA):
Primary master: 20 GB HD <-- Kubuntu has an 8 GB partition on this disk
Primary slave: 3 GB HD
Secondary master: CD-R/RW
Secondary slave: DVD-ROM

These devices all should be compatible with Linux, because I was running Red Hat 7 (2.4 kernel, I think) with no problems for a couple of years.  I've also been able to use the Knoppix LiveCD (2.6 kernel) with no problems.

Any suggestions as to work around this?

(Just as an aside: I also had the my system hang during "mounting root filesystem" when I tried to boot from the live CD.  This was solved using the "ide=nodma" parameter from the command line.)

---

### Post by gtmaneki on 2006-08-11
Well, I went home and tried disconnecting the 3 GB primary slave drive, and that seemed to keep the hardware detection phase from stalling.  

Now I have Kubuntu running :grin:, although I haven't tried reconnecting the other HD yet.

---

### Post by gtmaneki on 2006-08-12
Well, I've tried reconnecting my primary slave drive and Kubuntu hangs again.  This time it's at the "preparing hardware abstraction layer" phase of booting.  If the disk is not connected, things are fine, though.

Here's the setup (all IDE)
/dev/hda1 = Windows
/dev/hda2 = Linux
/dev/hdc = CD-R/RW drive
/dev/hdd = DVD drive

I'm not getting /dev/hdb, my 3 GB NTFS drive to show up.  I guess I'll have to take it out of its bay and look to see if the jumper is set properly.  Any other suggestions?

:confused:

---

### Post by gtmaneki on 2006-08-14
Well, I still can't seem to get /dev/hdb1 recognized. 

The jumper on the disk is set for "slave," I have edited fstab and mtab to add the proper information, and nothing seems to work.  The system boots fine if the drive isn't attached, and hangs if it is attached.

I guess it's time to upgrade to a bigger hard disk anyway, replacing /dev/hda and /dev/hdb with one disk bigger than both.  I sure hope this does it, and that Kubuntu is worth it.  I haven't had this much of a hassle during install since I first tried Slackware in '96.

](*,)

---

