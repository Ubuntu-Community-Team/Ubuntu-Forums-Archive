---
title: "Advanced Formatting System"
date: 2010-12-17
forum: Hardware
---

### Post by Red Kelly on 2010-12-17
Hi
Could someone please tell me how to format a WD20EARS into ntfs and get the best performance.
I understand it has 4096 byte sectors and should start at 64
Would this work?

```
mkntfs /dev/sdb -s 4096 -c 4096 -L multimedia 
```I ask because I'm creating (or at least trying to create)  a server for holding my movies, music and stream mythTV to an xbmc htpc and laptops (laptops have win7).
I have just got 2 WD20EARS one for the multimedia and another for backup. I am useing Ubuntu 10.10 64bit desktop edition.

I have looked around but haven't found anything that dosen't confuse the hell out of me, I am rather new at this if you hadn't guessed already so any help would be greatly appreciated.

---

### Post by Krytarik on 2010-12-18
Why don't you just use GParted (has to be installed) or at least "Disk Utility" (haven't used it for those operations so far) instead?

However, your command is correct, you even don't have to enter the -c and -s option, because these are the default values.

Greetings

---

