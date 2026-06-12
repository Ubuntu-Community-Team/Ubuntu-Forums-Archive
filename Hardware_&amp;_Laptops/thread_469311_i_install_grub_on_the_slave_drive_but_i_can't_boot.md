---
title: "i install grub on the slave drive but i can't boot in to Ubuntu??"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by ianchen06 on 2007-06-09
today i installed Ubuntu and i chose to install grub in the slave drive because this is not my computer so i want the grub be on the same drive as Ubuntu. After i installed them, i restarted the computer and then boot in to the slave drive (which i installed Ubuntu and grub in), and i chose to boot Ubuntu, but i said "Error 17   can not mount the selected partition", how do i solve this?? thanks

---

### Post by DagMan on 2007-06-10
It's going to have to do with which drive grub is telling it to boot.  I haven't run into this myself and am not sure if I can help or not, and hopefully someone else can if not.  To start can you please specify which partition the root folder of ubuntu is on, for example is it on the second drive and first partition?

---

### Post by confused57 on 2007-06-10
> **ianchen06 said:**
> today i installed Ubuntu and i chose to install grub in the slave drive because this is not my computer so i want the grub be on the same drive as Ubuntu. After i installed them, i restarted the computer and then boot in to the slave drive (which i installed Ubuntu and grub in), and i chose to boot Ubuntu, but i said "Error 17   can not mount the selected partition", how do i solve this?? thanks

If you get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...this is temporary, you'll need to make it permanent in your /boot/grub/menu.lst

If you don't get a boot menu, you can mount your root partition from the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then change your root entries to (hd0,x).

---

