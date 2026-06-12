---
title: "Partition layout"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by omargomez on 2009-11-06
Hi,

I'm installing Ubuntu 9.10 on my brand new Laptop. I'm planning to install several OS' on it. Using the legacy GRUB that was a matter of having a separate /boot partition and updating the menu.lst file when a new OS was installed, no big deal. But the new Grub2 boot loader got me puzzled. 

My question would be: In order for Grub2 to manage several OS', which partitions should I create in advance?. How is the updating procedure carried out?

Thanks,
--Omar

---

### Post by tommcd on 2009-11-06
It is not necessary to have a separate /boot partition when booting multiple distros. I boot several distros plus Windows on my desktop and I have never had a separate boot partition. This applies to grub-legacy and grub2.

As for the partition layout, what I do is to create a partition for the root partition for each distro I am installing. I also create a swap partition. All distros can share swap. I like to create a separate /data partition for my data. This way each distro's home partition is inside it's own root partition. This keeps all the .config files and directories separate so they can't conflict with the other distro's .config files.
The root partitions can be 10-14GB. This will be plenty for any distro. You could go with less if you are short on space. Make swap 1GB. If you plan to suspend to RAM, make swap at least as big as how much RAM you have. The /data partition can be the rest. 
You can create 3 primary partitions if you want. Make the rest logical.
To update the boot menu for grub2 you run:
```
sudo update-grub
```
See these references:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by omargomez on 2009-11-06
Thanks,

This is exactly the directions I was looking for.

--Omar

---

