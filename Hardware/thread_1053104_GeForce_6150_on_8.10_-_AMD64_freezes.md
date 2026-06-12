---
title: "GeForce 6150 on 8.10 - AMD64 freezes"
date: 2009-01-28
forum: Hardware
---

### Post by cwelch on 2009-01-28
I have a fresh, up-to-date (as of 1-27-09) install of 8.10 amd64 on my desktop which has an added in GeForce 6150 with the 177.82 driver pack. It also lists NVController Version 1.17 and Server Vendor Version 1.5.2 in the nVidia config program. MY problem is that I can boot the computer for a few minutes and after it loads to my desktop, the display jumbles up and the machine locks. Only the reset button or HPO will fix it. I thought it might have been a plugin issue with FireFox (since I'd just loaded the Adobe Flash and Gnome Flash plugins) and disabled everything in it. Nope. Even if I leave it sit idle (not long enough to go to sleep or even screen saver) it freezes. Also freezes during usage. Any ideas here? I'm trying to get this thing smoothed out so I can use it at work, and its not proving easy. This is my first major prob with anything Ubuntu that I haven't done myself, so I've had a wonderful success with it so far. Help me please!

---

### Post by Joe2Shoe on 2009-01-28
I have a HP dv9000z AMD Athlon 64 x 2 CPU with the nVidia GeForce 6150 video card, running Ubuntu v8.10 (Intrepid Ibex) with the 32-bit version.
Everything works fine.
Maybe you should install the 32-bit version, and not the 64-bit version of Ubuntu.
Good luck,
Joe2Shoe. ;)

---

### Post by cwelch on 2009-01-29
Does it particularly matter if the 32bit version runs on a x64 machine? I just kinda assumed.. I know windows doesn't really care, so I always kinda wondered..?

---

### Post by IQRules on 2009-01-29
Unless you have more than 4G and try to use certain RDBMS Oracle, DB2, memory extensive application. Otherwise, stay with 32-bit is perfect fine.

---

### Post by cwelch on 2009-01-30
Ok will give it a shot then. Like I said, its fresh so at least I don't have to lose anything! :)

---

### Post by theonhighgod on 2009-02-18
I've had this same problem just so you don't feel alone, not sure how to solve it, my graphics card is on board my asus motherboard, had problems with the "NV" free driver and the tainted nvidia driver. nv hardly ever crashes but won't go above 800x600 though does in plain debian lenny oddly, if any one else has this problem I'll post a solution if i find one,

good luck...

---

### Post by cwelch on 2009-02-19
Got to screwing around with it. Tunrs out windows started to do it, and then I was sitting idle at the GRUB screen and it did it again. Slapped a BFG NV 6200-based PCI in, and works like a champ now. Great big WTF but the new card is going great.

---

