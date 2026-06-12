---
title: "Grub Error 17?"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by dezgot on 2005-08-16
I've become quite used to the ease of installation of ubuntu, so when I tried to install it on my IBM 600E i  was expecting little to no problems, considering the laptop's popularity.  

However, after installation, GRUB begins to load off the hard drive (which is a 40gb hard drive, seems to be recognized fine by everything, including the ubuntu installer) and then halts, reporting that it had an Error 17.

I understand that this error means that Grub couldn't mount a partition.  I've ran through the ubuntu installation twice, here's how I have the partitions set up:

10gb windows system partition
~27gb shared fat32 partition

then I tell ubuntu to automatically partition the remaining space and it adds the following:
4gb ubuntu system partition, ext3
~240mb swap partition

Then installation continues normally, and when it reboots it has the error.  Any ideas?  Is there some paramater that I should have passed before installing?

I've installed  SuSE on this laptop before just because I didn't have an ubuntu CD at the time, and it worked flawlessly, but that was with a different hard drive and no preexisting windows partitions.

Help please?  O:)

---

