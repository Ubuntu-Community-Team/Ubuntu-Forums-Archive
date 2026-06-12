---
title: "External HDD Slower than on Windows"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by hermesrules on 2007-04-30
I decided to post a new thread since I am not certain my issues are the same as those affecting people who recently installed Feisty and found out their hda-s are not sda-s and all the other problems ensuing.

I am actually using OpenSuse 10.2 right now, and kernel is 2.6.18.8, which probably means that IDE drives are not treated as SATA. Therefore the separate thread...

I am using an external IDE hard drive, which I connect via USB 2.0 to my laptop (it's an older machine, so I need to use a PCMCIA USB card to get the high-speed USB transfers to work). It's a 250 GB drive, and I have three partitions on it, one FAT32, one NTFS, and one ext3. In Linux I have moved all my mail - more than 1 GB in size - (I use KMail) to the external drive to save space off of my laptop hard drive, which is only 30 GB, and linux gets 10 of those. I use a symbolic link in KMail's folder to have Kmail get to the mail files.

When I change mail folders (and I am only giving this as an example), KMail takes too long a time to display the contents of another mail folder. This did not happen when I had the mail on the internal drive. Hence my assumption that things are much slower on the external drive. Another example is copying - I only get about 1-2 MB/sec if I copy from a different partition or from (and to) the internal drive.

Of course, since I connect via USB, the three partitions are mounted as sda1, sda2, and sda3. I can't use hdparm to change anything, which is something well known to most of you already. In Windows speeds are much faster, practically equivalent to the speeds of the internal drive.

I get this problem with all the other distributions (Live CDs) I've tried - accessing the external HDD is always much slower under Linux...

Is there any remedy to this problem?

Thanks!

---

### Post by hermesrules on 2007-05-01
In fact, I just made an unusual discovery. It seems that once I had the ext3 partition mounted explicitly through /etc/fstab (instead of having the system do this automatically upon powering up the external HDD), transfer speeds improved quite a bit, more than 10 times!!!

I have no explanation of why this happens, so if anyone could offer one, I'll be very curious to hear it, for the sake of learning something new.

---

