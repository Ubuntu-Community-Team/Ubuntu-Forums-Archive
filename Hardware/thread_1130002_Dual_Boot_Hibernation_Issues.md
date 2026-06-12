---
title: "Dual Boot Hibernation Issues"
date: 2009-04-19
forum: Hardware
---

### Post by katalyst23 on 2009-04-19
So, I've looked around but haven't really found a solution to this, so maybe you guys can point me in the right direction.  :)

I am dual booting Vista and Ubuntu (Intrepid Ibex, 64 bit version) on my laptop.  They share a FAT32 data partition between them, it has my mozilla profiles on it, documents, etc.  I am very absent minded, so sometimes I will go to suspend or hibernate in one operating system, and then accidentally boot into the other when I reopen the laptop and select the wrong system in GRUB, which results in some pretty fubared data as you might imagine. 

Does anyone know of a way to possibly keep GRUB from popping up when one operating system or the other is hibernating?

---

### Post by katalyst23 on 2009-05-03
I found a solution to my problem, and I feel pretty silly since it is mentioned in the menu.lst file itself - I've just never paid attention to it.  If you change the 'default 0' option to 'default saved', and then place savedefault underneath the menu entries you want, it will boot from the last OS you booted into.  While this could be potentially annoying if you have just updated your kernel, it'll still keep you from fubaring your data!  Here's the link to the page in the fine manual: [TFM]("http://www.gnu.org/software/grub/manual/html_node/savedefault.html#savedefault")

---

