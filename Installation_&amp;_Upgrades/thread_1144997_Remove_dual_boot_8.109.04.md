---
title: "Remove dual boot 8.10/9.04"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by borislevalle on 2009-05-01
I had 8.10 on my computer, to my satisfaction. Since I have a troublesome VPN connection, I wanted to try Jaunty next to 8.10 before doing the final upgrade. I installed 9.04 next to 8.10, played around and got my internet connection to work. 

Now I want to remove 9.04 so I can upgrade 8.10 to 9.04. How can I uninstall 9.04? To be sure: 8.10 shouldn't be removed of course. I am not running a Windows/Ubuntu dual boot, so there's nothing I can do via Windows. Also, I do not have separate partitions.
Thanks, Boris

P.S. Ever since I installed 9.04, my 8.10 boot list has become a lot longer. Is that normal?

---

### Post by logos34 on 2009-05-01
Simply use Gparted in 8.10 to delete 9.04 partition (unmount it first).  (You say you "do not have separate partitions," but you must if you installed them side-by-side, right?)

Then run 

> sudo grub-install /dev/sda

this will re-write stage1 to the mbr of the disk, pointing to your 8.10 / partition boot menu. 

> **borislevalle said:**
> 
P.S. Ever since I installed 9.04, my 8.10 boot list has become a lot longer. Is that normal?

kernel update(s)?

---

### Post by CMJ Tech on 2009-05-01
> **logos34 said:**
> Simply use Gparted in 8.10 to delete 9.04 partition (unmount it first).  ?

Excuse me for interrupting your thread borislevalle.

logos34, can you explain how to unmount the partition?

Thanks

---

### Post by logos34 on 2009-05-01
sudo umount /dev/sdax

where x is 9.04 partition #

or right-click on it in gparted and unmount.  

(*If* it's mounted, which it may not be)

---

### Post by CMJ Tech on 2009-05-01
Thanks for the explanation!  :)

---

