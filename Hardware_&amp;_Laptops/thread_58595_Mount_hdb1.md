---
title: "Mount hdb1"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by rockett15 on 2005-08-20
Okay so here's what I have going on.

My Linux box has 2 hard drives in it:

[B]hda1 mounted to / (ext3)
hda2 mounted as SWAP[/B]


**hdb1 mounted to /home/srockett/Files (ext3)**

I have full permissions in my home folder and I need to have the hdb1 mount have the same rights. I am going to map a network drive to it from my windows drive and use it as storage.

What is the command I need to add to the /etc/fstab?

---

### Post by jasmuz on 2005-08-20
add this to your /etc/fstab list

/dev/hdb1        /home/srockett/Files  ext3  user    0       0

---

