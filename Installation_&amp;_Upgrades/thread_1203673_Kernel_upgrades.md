---
title: "Kernel upgrades"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-07-03
This week a major update arrived.  The major items in it were labelled as belonging to kernel 2.6.28-13, and the fact that installing them required a reboot implied that they were fundamental to the operating system, as would be expected of kernel upgrades.  However after installing these fixes uname still shows the kernel level as 2.6.28-11.

What were those fixes if they were **not** an upgrade to the kernel?

---

### Post by raymondh on 2009-07-03
> **jcobban said:**
> This week a major update arrived.  The major items in it were labelled as belonging to kernel 2.6.28-13, and the fact that installing them implied that they were fundamental to the operating system, as would be expected of kernel upgrades.  However after installing these fixes uname still shows the kernel level as 2.6.28-11.

What were those fixes if they were **not** an upgrade to the kernel?

Are you booting into 28-13?  Have you defaulted the boot option to 28-11?

---

### Post by jcobban on 2009-07-03
> **raymondhenson said:**
> Are you booting into 28-13?  Have you defaulted the boot option to 28-11?

Bear with me, I am not a Linux Guru.

I notice that the date stamp on /boot/grub/menu.lst is yesterday, but the file itself only refers to -11.  There are various ...-13-generic files are in /boot and dated 30 June, the date I installed the -13 update.  The date stamp on menu.lst is probably newer because I used gparted yesterday to move the boundary between 2 partitions on my drive.

Admittedly I have caused some problems for myself because I ran the Ubuntu install twice, which is why I have TWO bootable Linux partitions on the drive.  I would like to get rid of the second partition, but the grub boot-loader is in some sense pointing at the otherwise unused second partition, because I know it is the copy of /boot/grub/menu.lst in the second partition that is used by grub.  I would like to point grub back at the first partition, something that is probably trivial, but I haven't got up the nerve because if I screw it up, I may leave the system unbootable.

---

