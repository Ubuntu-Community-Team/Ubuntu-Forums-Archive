---
title: "Hardy Heron and irda on laptop"
date: 2008-06-13
forum: Hardware
---

### Post by Hillerd on 2008-06-13
I used this tutorial to enable irda on my Acer Travelmate laptop: [https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto).

It worked well on Feisty Fawn but not on Hardy Heron.

The command "cat /proc/net/irda/discovery" does not show that an IR device is visible.
The command "sudo modprobe irda0" returned the error
"FATAL: Error inserting nsc_ircc (/lib/modules/2.6.24-18-generic/kernel/drivers/net/irda/nsc-ircc.ko): No such device".
I checked the directory, the file is present.

Has anyone enabled the infra-red interface with his laptop in Hardy Heron an can give me some support?

Thanks
 Dietmar

---

### Post by dragonflyFZX on 2008-06-21
I have the same issue and desperately need my IR port. I have looked around to fix the error, but I have a slow internet connection at this moment. Did anyone else have a look at this issue and more success in fixing it?

---

### Post by dragonflyFZX on 2008-06-21
hi,

just to let know I found a solution

[http://ubuntuforums.org/showthread.php?p=5005854](http://ubuntuforums.org/showthread.php?p=5005854)

the software mentioned in the fifth message solved everything for me. I am writing this over a GPRS connection over IRDA from laptop to the net!!!

---

