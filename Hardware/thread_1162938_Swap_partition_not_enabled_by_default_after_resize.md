---
title: "Swap partition not enabled by default after resize"
date: 2009-05-18
forum: Hardware
---

### Post by nickfox on 2009-05-18
I have actually solved this problem but probably best to mention it.

I have: HP 2133 1.2ghz, Ubuntu 8.04.2 \n \l kernel 2.6.24-23-generic 1GBram

I had a phisical swap partition of 512mb from original default install. I had to resize this to install oracle-xe.

However after reboot the swap partition would not enable unless i manually hit swapon in the partition editor.

The problem is that the swap partition, in this case /dev/sda2 was referenced by its UUID in /etc/fstab, this seems to change or becomes in some way invalid after resizing and no longer worked.

I removed the UUID reference and replaced with /dev/sda2, and all is well.

Any one else experienced this issue?

---

### Post by logos34 on 2009-05-18
normally UUIDs don't change with resize, but only if you *format *the swap.  hmm...wonder what happened.

---

### Post by nickfox on 2009-05-18
Well i dont remember formatting the partition, but then i suppose i wouldn't have noticed as there is not data!

Is there a way i can view the the UUID for my swap partition?

that way i can resize the partition with the partition editor as i did before and keep a closer eye on the process, and obviously, check the UUID again after.

thanks

---

### Post by logos34 on 2009-05-18
sudo blkid 

also, I think gparted prints out the modified partition info after whatever process in the small details window below

---

