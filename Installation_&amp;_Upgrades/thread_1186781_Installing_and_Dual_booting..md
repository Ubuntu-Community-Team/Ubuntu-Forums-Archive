---
title: "Installing and Dual booting."
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Im A Ninja on 2009-06-13
Last night i partitioned my drive. Now i have C:,D: and K:. I want to put Ubuntu on k drive. The k drive is 20GB, is that enough to install ubuntu?

I had a problem installing last night. When i got to the bit where i choose where to install ubuntu. There were 2 options(can't remember excact wording):1.Use whole disk or 2.select partions.

They said somthing like that.

I chose the second one, i tried to select my newly made K(Ubuntu called it somthing else but i new it was my k because it was 20GB) drive but it said somthing like:no root system file is found.

Also when i install Ubuntu, i want to dual boot it with windows. that means when my computer starts i'll get an option to either run windows or ubuntu?

What file system does the drive i install ubuntu on have to be? i made K drive NTFS but i can change it.

---

### Post by merlinus on 2009-06-13
When you select the partition, iirc you can right-click on it, which will give mountpoint options.  Select / (root).  It will also make a /swap partition, which need not be more than 1.5G.

If the installation proceeds smoothly, it will set up a grub menu where you pick which os to run.

---

### Post by Im A Ninja on 2009-06-13
I select my partion, click next and it says, no root file sytem has been found or somthing like that.

and it doesn't give me a root mountpoint option. i can mount it as windows or dos. those are the only 2 options i have

---

### Post by Im A Ninja on 2009-06-13
I'm posting this using ubuntu off the cd. I've got the ubuntu installer open right now.

there is no root option. only boot, home, tmp, usr, var

what type of partion do i make it? ext2? ext4? fat32? what? i don't know which one.

---

### Post by merlinus on 2009-06-13
No / option?  Format it as ext3.

---

### Post by tosk on 2009-06-13
After you select the filesystem type for the partition you should be able to enter a mountpoint for it.

You'll need at least two volumes: one for root and one for swap.

---

### Post by Im A Ninja on 2009-06-13
OK thanks people, i have successfully installed ubuntu.

---

### Post by merlinus on 2009-06-13
Well done!  Enjoy...

---

