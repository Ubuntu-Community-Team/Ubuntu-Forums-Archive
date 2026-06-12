---
title: "UBUNTU 11.04 doesnt detect full amount of memory"
date: 2011-10-07
forum: Hardware
---

### Post by hatewindows on 2011-10-07
Running a Compaq CQ60 notebook--with 4.0 gigs of Memory--Ubuntu only reports 2.9 gig--any ideas! I dual boot to windows 7 and windows shows the full 4 gig......  Thanks all.

---

### Post by papibe on 2011-10-07
Did you install it with a working connection to the Internet?

Could you post the result of this command?
```
$ uname -a
```
Regards.

---

### Post by hatewindows on 2011-10-08
Linux mark-Compaq-Presario-CQ60-Notebook-PC 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by hatewindows on 2011-10-08
I installed the new memory with the Notebook off and a working connection to the internet!

---

### Post by LinuxFan999 on 2011-10-08
did you use the 32 bit or 64 bit version of Ubuntu?

---

### Post by hatewindows on 2011-10-08
32

---

### Post by LinuxFan999 on 2011-10-08
You will need the 64 bit version of Ubuntu in order to see all 4 gigabytes of memory.

---

### Post by Dy1anW on 2011-10-08
Or you can use the PAE aware 32-bit kernel, which will address your full memory, and you won't need to reinstall anything. If you don't mind a reinstall, then definitely go for the 64-bit.

---

### Post by papibe on 2011-10-08
> **LinuxFan999 said:**
> You will need the 64 bit version of Ubuntu in order to see all 4 gigabytes of memory.
That's not it. I can see all my 4Gb using a 32bit version.

However I have the [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") kernel. That it's usually installed when installing Ubuntu with a working Internet connection. For some reason it was not installed on hatewindows's.

Unfortunately, I don't know how to upgrade your kernel to a PAE version.

Hopefully, someone else will pitch in and help.
Regards.

---

### Post by Dy1anW on 2011-10-08
> **papibe said:**
> Unfortunately, I don't know how to upgrade your kernel to a PAE version.

Hopefully, someone else will pitch in and help.
Regards.

```
sudo apt-get install linux-generic-pae
```

I was under the impression that PAE wasn't installed by default... at least it wasn't on my laptop.

---

### Post by hatewindows on 2011-10-08
Thanks everyone!

---

### Post by hatewindows on 2011-10-08
Thanks for getting back to me so fast!  Have a great night!  Mark

---

### Post by hatewindows on 2011-10-08
Working like a charm now!! If i could only fix the other problem i have --My compaq CQ60 notebook which has 11.04 Ubuntu installed--Has a blinking Wireless light it blinks from Blue to orange each time i surf around the net.. In windows The blue light stay Blue Constant! Thanks for any help==The memory reading is perfect now!! Thanks so much!!! :)

---

### Post by wolfen69 on 2011-10-08
> **hatewindows said:**
> Working like a charm now!! If i could only fix the other problem i have --My compaq CQ60 notebook which has 11.04 Ubuntu installed--Has a blinking Wireless light it blinks from Blue to orange each time i surf around the net.. In windows The blue light stay Blue Constant! Thanks for any help==The memory reading is perfect now!! Thanks so much!!! :)

If it's not affecting your surfing, I wouldn't worry about it.

---

