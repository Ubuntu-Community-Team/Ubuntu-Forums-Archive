---
title: "Xubuntu from flash drive"
date: 2008-10-20
forum: General Help
---

### Post by rasmus91 on 2008-10-20
Hi, i just used my Ubuntu to Make a "bootable" flash drive with Intrepid Ibex Xubuntu. just for some... well call it experiments... but i've wanted to check out these other distros for a while. Anyway, i did this and now it seems i have a problem. first of all, my system won't automatically boot from my USB flash drive. so i tried installing the helping file (still dual booting with windows) but all i get is this message: > Installation: couldn't find any appropriate cd (this is when i press Demo and full install, help me boot...)

i guess this means it doesn't cd to the flashdrive.... what should i do about this, would be really nice if it would work...

so please help me!

Thanks Rasmus

---

### Post by ago on 2008-10-21
It means that grub4dos cannot see the specified ISO file, which is generally due to A) the drive not being accessible at boot time, B) the specified ISO being wrong (check menu.lst or press "E" in grub)

---

