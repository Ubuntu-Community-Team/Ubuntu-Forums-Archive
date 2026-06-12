---
title: "ubuntu won't share hard disk"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by david53 on 2009-10-05
I have recently acquired my first computer, and I am new to GNU/Linux systems. I have tried to create a multi-boot system on an 80 GB hard disk. This is so I can simultaneously explore more than one Linux O/S.

Here is the partitioning I created:

Extended  sda5 (holding only a swap sda2) 2.147 GB 
Primary    sda4 ext                                 29.8 GB    mounted at /home
Primary    sda3 ReiserFS                         25.0 GB                     /boot
Primary    sda1 ReiserFS                         25.0 GB                     /

After installing Ubuntu, I discovered that Ubuntu seemed to have grabbed all of the hard disk space and would not share. While running Ubuntu sda1 and sda 4 were both occupied. Perhaps this is because I mounted the partitions within Ubuntu? (I am here making a guess. During the installation Ubuntu seemed to insist that each partition be mounted.)

How can I format the hard disk so that Ubuntu only uses one partition, leaving the other partitions for another O/S?
Thank you for any help you can offer.

---

### Post by raymondh on 2009-10-06
> **david53 said:**
> I have recently acquired my first computer, and I am new to GNU/Linux systems. I have tried to create a multi-boot system on an 80 GB hard disk. This is so I can simultaneously explore more than one Linux O/S.

Here is the partitioning I created:

Extended  sda5 (holding only a swap sda2) 2.147 GB 
Primary    sda4 ext                                 29.8 GB    mounted at /home
Primary    sda3 ReiserFS                         25.0 GB                     /boot
Primary    sda1 ReiserFS                         25.0 GB                     /

After installing Ubuntu, I discovered that Ubuntu seemed to have grabbed all of the hard disk space and would not share. While running Ubuntu sda1 and sda 4 were both occupied. Perhaps this is because I mounted the partitions within Ubuntu? (I am here making a guess. During the installation Ubuntu seemed to insist that each partition be mounted.)

How can I format the hard disk so that Ubuntu only uses one partition, leaving the other partitions for another O/S?
Thank you for any help you can offer.

David53,

You're allowed 4 primary partitions or ... 3 primary + 1 extended.  An extended will contain AS MUCH logical partitions you and your OS or BIOS can take.

That said,  I would

- put /boot in a primary partition in front of the HD
- create an extended partition after /boot 
- Install all other distros (their roots') and swap as logical partitions inside the extended.

To create an extended .... boot into a live gparted CD or use the liveCD.  Highlight the partition > select NEW > allocate the size > EXTENDED > apply.  To create logical partitions, select the extended partition > new > size allocat > format ext3 or ext4 > apply.

Once the partitions are created (and using Ubuntu as an example) .... in step 4 of the install, choose manual > highlight the intended logical partition > edit > use as > select mount point (root) > format.

As a side note to using /boot ... and other info regarding multi-booting, see herman's site as a reference

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

Good luck, welcome to linux and the forums and happy ubuntu-ing :)

---

