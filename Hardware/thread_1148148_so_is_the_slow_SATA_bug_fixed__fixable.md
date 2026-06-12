---
title: "so is the slow SATA bug fixed / fixable ?"
date: 2009-05-04
forum: Hardware
---

### Post by remi_2 on 2009-05-04
Hi !

I've been suffering from very low SATA transfer rates (5Mb/s) on 8.04, 8.10 and now 9.04 on my asus M50sv laptop,

I believe it is the same bug as this one : 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119730](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119730)

I was wondering if there was a way to fix it by choosing appropriate bootparams or by recompiling the kernel by hand choosing the appropriate modules?

I've already reinstalled XP on the computer to be able to have correct transfer rates when needed... If I can't solve the SATA performance bug the next step is bye bye linux, which would be so sad :(

Cheers! and thanks for any help you may offer!

---

### Post by remi_2 on 2009-05-04
I read this page 

[http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)

and tried all combinations of bios setting enhanced vs. compatible for the SATA mode and combined_mode=libata vs. combined_mode=ide with no results so far.

The chipset on my laptop is an intel ICH8

Do you think keeping the 'compatible' mode in the BIOS and removing the libata from the kernel alltogether would be worth trying?

---

### Post by remi_2 on 2009-05-04
also tried this trick without success :

[http://ubuntuforums.org/showthread.php?t=435706](http://ubuntuforums.org/showthread.php?t=435706)

---

