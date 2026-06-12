---
title: "Merge / JBOD with a newly added HDD"
date: 2011-10-20
forum: Hardware
---

### Post by Catalyph on 2011-10-20
I have a Ubuntu 11.10 server system setup as a NAS / Media Server with 500 GB sata Drive
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5 LVM

I have just gotten another 500GB hdd and would like to append it to the first boot drive where Ubuntu is installed as JBOD or something else.

I do not want to format the drive as i spent a lot of time getting this machine up the way I want it.

I use the machine to download torrents using Transmission and store my Media 
I would be great if I can just add the second disk to make the first disk look larger and have more storage space, unseen by the applications.

I looked around on google and such but only found how to actually add the HDD as a second drive

---

### Post by Catalyph on 2011-10-21
Nobody has any input on this ?

---

### Post by digitalslave on 2011-10-21
you will need LVM support.

[http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

[http://www.randombugs.com/linux/howto-extend-lvm-partition-online.html](http://www.randombugs.com/linux/howto-extend-lvm-partition-online.html)

---

### Post by Catalyph on 2011-10-21
Thank you!
The Partition sda5 is LVM

---

