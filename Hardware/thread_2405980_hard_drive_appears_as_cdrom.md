---
title: "hard drive appears as cdrom"
date: 2018-11-14
forum: Hardware
---

### Post by Skaperen on 2018-11-14
i have an old hard drive i just plugged to see what was on it from years ago.  it is 320GB and was bought back when 320GB was the largest available for USB.  it is a USB powered Western Digital brand drive.  it shows up as two devices: /dev/sdd (because i already have 3 drives on this laptop) and /dev/sr0.  what i am wondering is how it can appear as two devices, how it can appear as a cdrom, and if there is a way that i can put my own cdrom image on there and have it show up as /dev/sr0.

---

### Post by tea for one on 2018-11-14
If my memory serves me well, I think that your hard drive has some sort of partition (/dev/sr0) which was sometimes used for creating a password to protect the data which would sit on your /dev/sdd.

Approx 10 years ago, Sandisk Cruzer USB sticks used to come bundled with a similar system called U3 where you could run portable applications on Windows machines.

If you have Gparted installed, you could see more details about the partitions .

---

### Post by Skaperen on 2018-11-14
thanks.  i do have a number of _GPT_ tools to look around with.  [FONT=courier new]gparted[/FONT] is not among them but i can install it.

---

### Post by tea for one on 2018-11-15
Again, if I remember correctly, these external hard drives/USB devices had a separate partition that looked like it was a CD ROM to allow password protection.

I'm pretty sure that the firmware on the drive was written in such a way that the CD partition "automounted" so that the password log in was presented to the owner before access to the data on the rest of the device.

I reckon that it is something to do with boot order where, previously, old style CDs always used to boot first (i.e. before external HDDs).

I bought a Freecom Toughdrive (external USB) years ago and that had a CD style partition. I found a utility on their website that allowed the removal of the small password partition and turn it into a regular USB drive. I still use it today for backups.

Do Western Digital have any info on their website for your device?

---

### Post by Skaperen on 2018-11-15
the [www.wd.com](www.wd.com) site is worhless for finding good technical info.  the google shows a little more.  there are products specifically sold as cdrom and dvdrom configurable emulators.  among the limitations, the .ISO file must be in partition 1 which must be in NTFS format.  partition 1 must be findable in an MBR partition table (so i presume a hybrid would work).  the device had its own LCD display and some buttons to choose which .ISO file to use.  typical suit-and-tie downgraded technology.

i would only need this for some older computers that can't boot from USB except for CDROM.  newer .ISO image files can also boot as hard drives (i used to convert ISOs to do thus, years ago.  CDROM and DVDROM is dead, IMHO.  i omitted them and got an extra hard drive in my last laptop order.  so thinking about this, there's not much i need this old ha drive for, but it would be nice to have something that older computers can boot from that i can bring to where it can help install/rescue Ubuntu.

---

