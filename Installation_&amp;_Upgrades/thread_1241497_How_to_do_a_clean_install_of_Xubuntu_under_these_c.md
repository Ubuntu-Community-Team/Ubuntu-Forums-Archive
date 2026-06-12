---
title: "How to do a clean install of Xubuntu under these conditions"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by lushan on 2009-08-16
I currently have a dual boot Windows XP / Ubuntu.  I would like to do a clean installation of Xubuntu into Ubuntu's partition, wiping Ubuntu at the same time.  Is there any easy way of doing this?

I do not want to do aptitude Xfce and login a different session.  I also cannot repair Windows XP boot loader because the Recovery Console asks for a password.

Thanks in advance.

---

### Post by Partyboi2 on 2009-08-16
Hi, you should be able to choose the "manual" partitioning option during the install and select your current root partition and reset the mount point to / as well as tick the box to format. This should install Ubuntu to  the Xubuntu partition.

---

### Post by lushan on 2009-08-16
So I double click the /dev/sda5 (currently ext4 Ubuntu), choose a drop down option for "Use as", check the "Format the partition" box and change the "Mount point" to /?

What does "Mount Point" mean?

I also have a /dev/sda6 marked as type swap.  What is that?

Thanks.

---

### Post by Partyboi2 on 2009-08-16
> So I double click the /dev/sda5 (currently ext4 Ubuntu), choose a drop down option for "Use as", check the "Format the partition" box and change the "Mount point" to /?
Yes that is correct. A mount point is where the file system will be mounted.

>  I also have a /dev/sda6 marked as type swap.  What is that?
The swap-partition is something like the  page files under Windows.
You can read more about swap from here:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by lushan on 2009-08-16
Thanks.

I would like to adjust my swap.  But I ended up with the old one marked as linux-swap and a newly allocation swap.  Is there a way to merge them into a new swap area?

---

### Post by lushan on 2009-08-16
I deleted both swap areas and try to make a new one.  I hope this was not a wrong move.  Which type of partition should I use for a swap?  primary?  logical?  Beginning? End?

---

### Post by Partyboi2 on 2009-08-16
You would use a "Swap Partition" for the swap, you can either have it as a primary or logical partition.

---

