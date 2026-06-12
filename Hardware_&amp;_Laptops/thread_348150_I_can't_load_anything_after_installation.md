---
title: "I can't load anything after installation"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by Brujulo on 2007-01-28
Hi!
I got an old laptop fujitsu siemens C1010 (PIII 1.2, 256RAM...) which have some problems booting. For exemple, it can boot from a Windows XP cd (first version) but it can't from a cd with Windows XP SP2 (in other pc's runs correctly). 
I got boot from Ubuntu CD and I installed it succesful. But when i reboot without cd, the laptop don't find any boot system. It ask me about any cd or something because it doesn't find nothing at HDD (and Ubuntu still installed at the HDD). However, if i put the Ubuntu cd and choose start from hdd (last option) it loads Ubuntu fine.

I have updated the BIOS and my version of Ubuntu is 6.10 .

Any suggestion?:confused: 

Thanks.

---

### Post by aysiu on 2007-01-28
I'm not sure what happened, but have you tried reinstalling Grub?

I think you can do that by selecting "repair an installation" from the Ubuntu CD boot menu, answering all the initial questions, and then choosing to restore Grub to the MBR.

---

### Post by Brujulo on 2007-01-28
Thanks for your answer aysiu.

I don't find any repair option on the live-cd menu (only install ubuntu, safe graphics, memory test and start from hard disk -with this option I can load Ubuntu-). 
But I was trying the super grub program ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)) which boot a minimal grub (I think that the progam neither runs correctly) and I use this command:
*root (hd0,0)* (I think that linux is installed in hd1 but the program says "unkown format" in 1 and 2 and doesn't says this with hd0)
*setup (hd0) *

Seems succesful but the problem persists.

Maybe I should try with Mandriva.

---

### Post by aysiu on 2007-01-28
> **Brujulo said:**
> 
Maybe I should try with Mandriva. Go for it. Best of luck. And please do report your progress. It's possible someone else may be able to jump in and offer some good solutions. Or, if you find one on your own, it'd be great to have as a research for any future users who may encounter the same problem.

---

### Post by Brujulo on 2007-01-29
Finally I installed Mandriva One 2007 and, fortunately, lilo boots fine without cd.

Maybe this laptop have problems with grub. It's a bit weird, I think.

Thanks!:D

---

