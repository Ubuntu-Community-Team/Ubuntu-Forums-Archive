---
title: "2nd SATA HDD is not recognized!  8.04"
date: 2008-05-03
forum: Hardware
---

### Post by Brasilwarrior on 2008-05-03
Hello All,

I am facing a very strange issue with my new installation of ubuntu hardy. 

In BIOS my 2 SATA Fujitsu 250GB HDD are recognized correctly. In the Live CD only ony HDD is recognized. If I change the boot order 
the other drive is recognized. 

I have used also fdisk -l same result as described above. I have also tried to write the UUID directly in the fstab without any sucess. 

A installation on one of the HDD drives not chnage the behavior, 
during the boot I could see that the 2 drives are listed. 

Mainboard VIA EPIA EX15000G
HDD MHX2250BT

Thanks for any help.

Best Regards

Brasilwarrior

---

### Post by Brasilwarrior on 2008-05-04
Hello All,

I have added all_generic_ide to my boot/grub/menu.lst and now the second HDD is recognized.

What is the disvantage to use this seeting in grub?

What exactly this command does?

What irqpoll do?

Thanks

Best Regards

Brasilwarrior

---

