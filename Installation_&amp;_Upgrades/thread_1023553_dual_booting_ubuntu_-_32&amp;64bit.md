---
title: "dual booting ubuntu - 32&amp;64bit"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by Stargazer989 on 2008-12-28
64bit isn't working all too well on my laptop(Gateway MC7801u) so i asked in the official ubuntu channel on FreeNode, a guy named 'stan' said that i should try ubuntu 32bit using the alternate text install CD... but idk how to do this because only one can have / as root. this or i'm being a noob.

i have some unallocated space (about 75gB) and i partitioned off about 25gB for this new install. any ideas how i can get ubuntu to dual boot with the same version but in 32bit ?

thanks in advance.

~stargazer989

---

### Post by parajuito on 2008-12-28
Just boot from the installation cd 32-bits , when you get to the partitioner then you select whatever you want, you can select it to install in all the free space that is on your computer use all space or you can select any partition you want. If you want to dual-boot 32-bits and 64-bits install the 32-bits version with the installation cd in the partition you created.

---

### Post by Stargazer989 on 2008-12-28
so nothing will flip out because i have 2 of the same ubuntus(aside from the 32 and 64 bit difference)?

---

### Post by cariboo on 2008-12-28
If your laptop is locking up using the 64bit version, it will more than likely do the same thing running a 32bit version, what you have is a hardware problem, not software.

Have you tried any of the noapic options? Add noapic to the kernel line in /boot/grub/menu.lst and see if that helps your problem.

I would suggest getting in touch with the manufacturer of your laptop, and se what they have to say about the bios problem.

Jim

---

### Post by Stargazer989 on 2008-12-28
what bios problem ? o.o
what exactly does 'noapic' do ? (i like to know these things before adding them)

thanks.

there are warning signs, i guess you call them. the screen dims every so slightly and the dim starts to waver somewhat.

---

