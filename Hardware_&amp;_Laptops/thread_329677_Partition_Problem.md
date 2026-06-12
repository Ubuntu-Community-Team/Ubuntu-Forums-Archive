---
title: "Partition Problem"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by Zav3 on 2007-01-02
I have a somewhat complicated problem.

So I installed linux about a week ago, and have dual-boot with XP, and had some problems and ended up installing it twice and on my secondary hard-drive, which I did not want to do. Now I disabled the grub loader with this MS-DOS installer disc I burned, it was a Freedos. 


Then in the linux disc I went and deleted the partitions of linux, with the intention of reinstalling on to just my primary hard-drive so as to let windows and linux share the same one. I deleted the partitions on the secondary hard-drive fine, but when I deleted the linux partion on my primary, and resized the windows partition to full, it somehow got filled up with something. (I am thinking it is the linux data, but do not know how that can happen. 

Now, in all the partition managers I try, it says the hard-drive is the size it is (80g), but that only 13g is free. (there should be around 40g free, though)  And when I click on the properties of the drive from My Computer in Windows, it says the drive is only 35g big.

Did the partition somehow not get fully deleted?

---

### Post by michaeljustman on 2007-01-02
Are you sure that you resized your Windows partition to take up that space?

What tool did you use to resize your Windows partition?

---

### Post by bigken on 2007-01-02
download and burn the gparted liveCD boot from it this will show you what partitions you have and allow you to resize them ;)

---

### Post by Zav3 on 2007-01-02
I used the partition editor on the ubuntu live cd. Gnome Partition Manager.

I will give gparted a try

---

### Post by Zav3 on 2007-01-02
Ok, the gparted live cd worked. It displayed the partition as the should have been, I got it all straightened up. Thank you.

---

