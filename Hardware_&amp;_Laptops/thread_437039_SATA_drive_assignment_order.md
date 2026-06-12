---
title: "SATA drive assignment order"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by ianare on 2007-05-08
I have a promise PDC40718 SATA controller hooked up to 4 drives. My problem is the drives do not get assigned device names in the same order they are hooked up.
On boot, the controller gives me a message similar to this:

ID 0 - wd5000aaks
ID 1 - wd5000aaks
ID 2 - st35006414s
ID 3 - st35006414s

But dmesg looks something like this:
ID 0 - wd5000aaks
ID 1 - st35006414s
ID 2 - wd5000aaks
ID 3 - st35006414s

It will do this consistently, if I swap cables around the drive order will either not change, or change but still not be correct.

Any ideas?

---

### Post by psusi on 2007-05-08
Why is this  a problem?  This is behavior is to be expected.

---

### Post by Spartan.II.117 on 2007-05-08
i suggest using the uuid of the drive in your fstab file to assign the drives where you want them.

---

### Post by pirothezero on 2007-05-08
> **Spartan.II.117 said:**
> i suggest using the uuid of the drive in your fstab file to assign the drives where you want them.
Sorry to bother on the thread but I sort of have the same issue I think when I reboot they swap my root and storage devices and before i never had this problem. 

How does one restore uuids if they tore them out of fstab?

---

### Post by Spartan.II.117 on 2007-05-08
look here:
[http://www.linuxquestions.org/questions/showthread.php?p=2733004](http://www.linuxquestions.org/questions/showthread.php?p=2733004)
i dont have time to check through this whole thing right now.

---

