---
title: "Help partioning hardrive"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by haran_hockey on 2008-12-19
I've downloaded the ubuntu 8.10 cd and am at the partitioning stage. I chose manual partition. My main partition is windows xp (C:\) and I have another partition on drive E:\ (vista). What I want to do is delete the vista partition and put ubuntu on it. So right now there is 23 Gb allocated to vista. So what I did was delete the partition and then created a new one. What I need to know is:

Type of partition: logical or primary(I made the vista a primary fyi)

Location for the new partition: beginning or end

---

### Post by taurus on 2008-12-19
If you want to install Ubuntu on that harddrive, wiping out vista, just tell the installer to use the whole disk.  It knows what to do.  Otherwise, you need at least two partitions:  one for / and a smaller one for swap.

---

### Post by haran_hockey on 2008-12-19
I already have 2 partitions. one for xp and one for vista but I want to deleted teh vista one. Do I still do what you said?

---

### Post by wpshooter on 2008-12-19
You need 3 partitions.

/ = root type ext3 make bootable - about 15gb if possible
/home = home type ext3 - remainder of drive after root & swap
/swap = swap - about twice the amount of your RAM size.

If possible I would make all 3 primary.  I think beginning is the default, use that.

---

### Post by haran_hockey on 2008-12-19
I just want to swap vista with ubuntu. So vista is deleted and ubuntu takes up same amount of space as vista previously did.

---

### Post by wpshooter on 2008-12-19
I believe that you need MANUALLY partition the drive as I mentioned above.

---

### Post by haran_hockey on 2008-12-19
I need to know exactly how and what to do. What type and do I choose begninning or end.

---

### Post by logos34 on 2008-12-19
Primary partition

/

ext3

'beginning'

then make a small swap (primary, linux-swap, mounting at /swap)

---

### Post by haran_hockey on 2008-12-19
how do i make the small swap. This is my first time installing ubuntu. And do i delete my vista partition first or 'edit it'. When I click on forward, it says you have not selected a partition to use a swap space.

---

### Post by jerome1232 on 2008-12-19
If you actually boot up from the live cd and upload screenshots (or the output of sudo fdisk -l) of gparted we can probably give much more clear and consice directions on what to format and create.

---

