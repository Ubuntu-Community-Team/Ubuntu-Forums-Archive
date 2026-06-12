---
title: "resize2fs fails with &quot;No space left on device&quot;"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by CombinedEffort on 2009-05-06
Hi,

I have an Acer Aspire One I'm trying to put 9.04 UNR on. It currently has the following:

/dev/sda1 40MB /boot ext2
/dev/sda2 256MB swap
/dev/sda3 7.23GB / ext2

with Gentoo installed on /dev/sda3. I wanted to resize sda3 to about 5GB and install UNR on the remaining 2.23 GB. I booted off a 9.04 UNR USB Drive and started QParted, but this failed to resize. After digging through the log, it looks like it failed on:

resize2fs /dev/sda3 5486197K

The Gentoo install is 'only' taking up about 3.5GB of the 7.23GB, so it 'should' be able to resize it...What gives?

Cheers,

Rich.

---

### Post by CombinedEffort on 2009-05-06
I gave up with this in the end and just tar'd /dev/sda3 off to another device, deleted & recreated the /dev/sda3 partition as a 4.5GB, formatted and tar'd it back on.

Cheers,

Rich

---

### Post by dandnsmith on 2009-05-06
I was bashing my head against this one a couple of days ago.

When you use the dd to create the USB device from the .img file, what they don't tell you is that it screws the partition record to show that the (limited) content fills the whole partition - in my case it was a 4G partition pretending (after the install) to be less than 1G.

I then copied the whole content as a file hierarchy, re-partitioned and formatted the USB device, copied the content back, and played with the files and sizes as I wanted. There may be an easier way, but I tried the resize etc in vain.

---

