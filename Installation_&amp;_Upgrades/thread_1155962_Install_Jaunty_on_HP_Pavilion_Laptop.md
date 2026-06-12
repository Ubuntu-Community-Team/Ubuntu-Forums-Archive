---
title: "Install Jaunty on HP Pavilion Laptop"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by rausuar on 2009-05-11
Hi,

I am using an HP Pavilion dv2872 Laptop, with Vista and Jaunty (installed inside Vista with Wubi).

I would like to install Ubuntu with a separate partition (using Ext4) but I am not very sure how to do it.  As you know, this Laptops come with a Vista partition and a Recovery partition.

Could someone explain me how to install Jaunty without messing the other partitions, or either give me a link to some page which explains it?

Thanks!

---

### Post by Triptol on 2009-05-11
There is a dual boot manual out there: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) which might be helpful.

Personally I would do the following:
[LIST]
[*]Use a windows tool (if possible) to shrink your main partition and free up some room at the end of the disk (not at the beginning!).
[*]Boot from an Ubuntu disk and install on the empty space.
[*]Let Grub install in the MBR.
[/LIST]

---

### Post by rausuar on 2009-05-13
Thanks!, the guide was very helpful, at the end, I was able to use the Vista partition manager (as described in the guide) to shrink its partition and create an empty unalocated space, where I after installed Jaunty without any problems and following the normal procedure.



> **Triptol said:**
> There is a dual boot manual out there: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) which might be helpful.

Personally I would do the following:
[LIST]
[*]Use a windows tool (if possible) to shrink your main partition and free up some room at the end of the disk (not at the beginning!).
[*]Boot from an Ubuntu disk and install on the empty space.
[*]Let Grub install in the MBR.
[/LIST]

---

