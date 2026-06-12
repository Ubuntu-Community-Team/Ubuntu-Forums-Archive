---
title: "Increasing size of Ubuntus partition"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Qwertylol on 2009-02-07
Sorry if wrong place.

OK, so I have about 3 gigs of disk space I removed from vista. I want to move it to ubuntu, how can I do this? I don't have the option under disk management in vista or gparted in ubuntu...

Installed using ubuntu live cd.

Thanks.

---

### Post by overlord.gaurav on 2009-02-07
You can install gparted on your ubuntu system.
And once installed you edit the partition table from there.

Edit:
To install gparted, open a terminal a type:
```
 sudo apt-get install gparted
```

To run gparted type:
```
 sudo gparted 
```

---

### Post by avtolle on 2009-02-07
You will need to do this from the Live CD, as the system partition is mounted when using Ubuntu and you cannot resize, etc., a mounted partition. You could also use the gparted Live CD for this as well. Good luck, and post back with questions.

---

### Post by Qwertylol on 2009-02-08
> **avtolle said:**
> You will need to do this from the Live CD, as the system partition is mounted when using Ubuntu and you cannot resize, etc., a mounted partition. You could also use the gparted Live CD for this as well. Good luck, and post back with questions.

I put in the CD then what?

---

### Post by earobinson on 2009-02-08
reboot your computer, boot of the live cd (this makes no changes) then run gparted from there!

---

### Post by Qwertylol on 2009-02-08
I'm on ubuntu live cd, gparted but when I right click ext3, and click extend it doen't let me increase its size, how do I do it?

The free space is before the "ubuntu partition" (the one that collectivly contains the two ubuntu partitions)

---

