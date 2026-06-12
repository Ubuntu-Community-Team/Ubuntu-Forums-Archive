---
title: "Need Help Please!"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by h8tisf8t on 2007-12-22
I'm trying to dual boot. I have Vista installed on drive c and it has d as its recovery. e to i are removable media drives and j is the new hard drive that i installed ubuntu 7.10 on. vista no longer shows drive j. im trying to use easybcd to dual boot but it keeps refering to linux as being on drive c. how can i get it work? it shows that linux is installed. on the add entry screen under linex it shows drive 0 is where linux is and drive 1 is where vista is.

---

### Post by Existentialist on 2007-12-22
If you did a normal install of Ubuntu, it should have installed the bootloader GRUB on to the same hd as Ubuntu.  If try booting from the hd with linux on it GRUB should come up and it probably sees the windows install and will let you choose vista or Ubuntu.

---

### Post by h8tisf8t on 2007-12-23
doesnt work but i am able to use easybcd just have to keep editing the linux boot location

---

### Post by Sef on 2007-12-23
From the Terminal (Applications > Accessories > Terminal), type this command and post the results here:

```
sudo fdisk -l
``` (That's a small -L.)

That will show what your partitions are.

---

