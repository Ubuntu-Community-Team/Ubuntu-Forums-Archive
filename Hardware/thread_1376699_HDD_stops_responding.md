---
title: "HDD stops responding"
date: 2010-01-09
forum: Hardware
---

### Post by fjanoos on 2010-01-09
Hello,

I have recently started to experience a strange problem with one of the hdd's on my computer  (Pentium-4 3GHz, 3GB RAM, NVidia 6800 Gfx card, Ubuntu 9.10, kernel 2.6.31-15)
 
A few days ago, when I logged in, I could not see one of the hdd installed (Seagate Baracuda 3200, 200GB PATA) - in the sense that not only I couldn't access it's file system but it would not show up either in fdisk or even on lshw. 

After I restarted the machine - fdisk listed the hdd but I couldn't mount its filesystem. Also, "smartctl -i /dev/sdb" returned the following message:

> Short INQUIRY response, skip product id

lshw simply showed that a disk was attached to the ide port but would not give any other details about it. 

I then shutdown my computer, removed the hdd and reconnected it back and it started working fine. 
However, again this morning, the same problem occurred.

This is a 5 year old machine and I have never experienced this problem before. I have no idea of what the problem could be - the hdd seems to be healthy with no bad sectors. 

Any ideas/suggestions would be appreciated ! 

Thanks

---

### Post by scytherswings on 2010-01-09
So you have no way of getting a SMART report? Or is that what you mean when you say "healthy?" A 5 yr old HDD is probably at the end of its warranty depending on the manufacturer...

---

### Post by fjanoos on 2010-01-15
Hi,

If I physically disconnect and reconnect the HDD - it starts working fine and I can read its SMART status (which shows as healthy). I also ran the "Extended Self Test" that comes with gsmartcontrol - which gave the HDD a perfect bill of health. All the data is accessible and intact. 

However, again after few hours of letting the machine idle - the HDD stops responding and is not detected. Could be a mobo problem ?

Thanks,
-firdaus

---

