---
title: "[SOLVED] Resizing?"
date: 2008-09-06
forum: General Help
---

### Post by Yezinki on 2008-09-06
Hi,

Can one resize a drive that has already been partitioned.......dual boot partitioned?

Thanks!

---

### Post by dark_phantom on 2008-09-06
Yes, kind of tricky since Windows is pretty sensible with this.  What I do, and this is just me.  I would back up my linux partition, then use whatever software in windows and resize it from there.  Or you can just wipe your linux partition then resize.  Either way you have your data and just copy it back when you have the scheme you like.

---

### Post by cdtech on 2008-09-06
Sure, you would have to use your Live CD and open "gparted" then you can manipulate your partitions.

---

### Post by rossjman1 on 2008-09-06
> **cdtech said:**
> Sure, you would have to use your Live CD and open "gparted" then you can manipulate your partitions.
or just sudo apt-get install gparted

---

### Post by Yezinki on 2008-09-06
sudo apt-get install gparted 

would just allow to have look wont allow to resize??

Thanks!

---

### Post by Yezinki on 2008-09-06
How does one use Live CD to resize?

---

### Post by Shazaam on 2008-09-06
Don't forget to defragment Windows before resizing (best if done in  Safe Mode). And remember the Windows 50 50 rule- Windows free space should equal Windows used space on the Windows partition. Say 20gig used =20gig free results in a 40gig Windows partition size.

---

### Post by cdtech on 2008-09-06
> **Yezinki said:**
> How does one use Live CD to resize?

Live CD is just like using your desktop. Select "try" and when you get to the desktop you can open "gparted" under "System > Admin > Partition editor".

The reason I said Live CD is because you cannot manipulate a mounted partition. Using the Live CD you can manipulate any drive within your system.

---

### Post by Yezinki on 2008-09-06
Thanks cdtech!

---

### Post by cdtech on 2008-09-06
Your welcome.

Good luck.........

---

