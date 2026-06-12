---
title: "Installing Boot Partition on a Separate Disk"
date: 2015-10-25
forum: Hardware
---

### Post by cobalt2 on 2015-10-25
I am setting up a SSD for a Lubuntu installation. The disk will be a RAID 0 array. I want to avoid putting the boot partition on this disc, because for every x MB of space used by the boot partition there will be an equal amount of space left unallocated. GRUB doesn't understand RAID, so the boot partition can't be included in a RAID array. Is it possible to installl the boot partition to it's own drive, a flash drive or a hard drive for example?

---

### Post by yancek on 2015-10-25
> Is it possible to installl the boot partition to it's own drive, a flash drive or a hard drive for example? 		

Yes it is.  You will need to select the Manual/Something Else option  during the install to select the boot partition.

---

### Post by weatherman2 on 2015-10-26
But /boot can be very small - 100MB should be fine.  if you think it's worth it to add the complexity of another drive in order to add that much extra space to your array, then go for it.

Yes, you could use a USB flash drive for /boot  as long as your system boots reliably from USB.

---

### Post by cobalt2 on 2015-10-26
The unallocated space is 100 MB, only 0.17% of the space on my 120 GB SSD, so I decided to create the boot partition on it. Now I have a quirk. The sd numbers are not in logical order.

Terminal Output:

Device Boot           Start          End              Blocks     Id         System
/dev/sdd1           196608              117229567  58516480     5      Extended
/dev/sdd5          7700480           113227775     52763648     fd  Linux raid autodetect
/dev/sdd6          113229824   117229567     1999872        fd    Linux raid autodetect
/dev/sdd7          198656                7698431             3749888        83   Linux raid autodetect

Partition table entries are not in disk order

How do I go about fixing this?

Sorry about the formatting of the terminal output. I tried formatting it manually, but vBulletin keeps stripping my formatting.

---

### Post by weatherman2 on 2015-10-26
Why do you need them to be in order?  Use UUID or labels to reference then instead of device IDs that can change.

---

### Post by cobalt2 on 2015-10-26
Where to find the UUIDs?

---

### Post by cobalt2 on 2015-10-26
I used ```
sudo blkid
``` to get the UUIDs. Now when I use mdadm to create a RAID array, it says mdadm is not installed. I was using it yesterday without having to install it. Now Terminal says 'The program mdadm is not installed.' When I type apt-get install mdadm, it's offering me the wrong package. How to get mdadm?

---

