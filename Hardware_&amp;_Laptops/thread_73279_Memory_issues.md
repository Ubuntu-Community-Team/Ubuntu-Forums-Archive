---
title: "Memory issues"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by niw_uk1964 on 2005-10-08
My 5.04 installation won't recognise my full complement of RAM.

I have an MSIK7TPro266-RU motherboard with 1.5GB of RAM organised in 3 sticks of 512MB. The bios recognises the RAM without a problem but when I boot into Ubuntu it only sees 885MB. Any ideas? TIA.

My system is as follows:

Mobo as above
Athlon XP2400+
Western Digital hdd on IDE1-master
Turtle Beach Santa Cruz sound card
Iwill scsi adaptor in pci slot 2
HP9600 cd-rw drive on the scsi adaptor
Yamaha 3200 cd-rw drive on IDE-2 master
Matrox G450
D-Link 530TX nic in pci slot 5

---

### Post by DJ_Max on 2005-10-08
The Ubuntu kernel default setting has the 1GB limit hold. There are two ways I know to disable this, here's one
[http://ubuntuforums.org/showthread.php?t=55570](http://ubuntuforums.org/showthread.php?t=55570)

---

### Post by niw_uk1964 on 2005-10-09
Thanks very much for th epointer. I'll give it a whirl. :D

---

### Post by niw_uk1964 on 2005-10-09
Brilliant...thanks! :D 

That's fixed it...kind of. It will see 1012MB with 2 sticks of 512 in but, the system crashes when booting into Ubuntu with 3 sticks in. It gives a kernel panic. I'll post the output here later.

---

### Post by DJ_Max on 2005-10-09
[QUOTE=niw_uk1964]Brilliant...thanks! :D 

That's fixed it...kind of. It will see 1012MB with 2 sticks of 512 in but, the system crashes when booting into Ubuntu with 3 sticks in. It gives a kernel panic. I'll post the output here later.[/QUOTE]
It may be a bad RAM, or incorrect RAM type.

---

### Post by Emerzen on 2005-10-09
I believe you need the 686 kernel if you have > 1GB of RAM.  Go to synaptic and find linux-image-686...then install it.  When you reboot select this kernel, it won't remove your old kernels-you'll have the option from GRUB to boot any kernel you want, and see if that works.  By the way, some 686 kernels have 'smp' at the end...only select this kernel if you have dual core or Hyperthreaded processor.

---

### Post by niw_uk1964 on 2005-10-09
[QUOTE=DJ_Max]It may be a bad RAM, or incorrect RAM type.[/QUOTE]

I think yo may be right - if I reduced the memory clock speed to 100Mhz then it was recognised and the system ran fine then.

Thanks guys - open source is the way to go. :D

---

### Post by DJ_Max on 2005-10-09
[QUOTE=niw_uk1964]I think yo may be right - if I reduced the memory clock speed to 100Mhz then it was recognised and the system ran fine then.

Thanks guys - open source is the way to go. :D[/QUOTE]
I look forward to comments like that. No problem.

---

