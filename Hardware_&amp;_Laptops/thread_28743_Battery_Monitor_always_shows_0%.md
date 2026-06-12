---
title: "Battery Monitor always shows 0%"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by oden08 on 2005-04-21
Just got an old Compaq laptop from a friend (Presario 1600 - PII). Upon loading up on Ubuntu I am having a few issues which I was wondering if anyone can help me with.

The battery monitor is always showing 0% even though when I am running it from the battery and when it is plugged in it still shows the battery monitor (rather than it is plugged in). I searched but couldn't find anyone who is having this issue so wondering if anyone could help me.

I am also having trouble with my PNY flash drive auto-mounting but I found some stuff on that which I will be trying.

Finally, my sound isn't working. I know the module which I need to be using (snd-nm256, because I have a NeoMagic 256) but don't know where to go from there. I was reading a doc which referenced an "ALSA-Configuration.txt" file but I can't seem to find that.

Any and all help would be appreciated. Other than that I am amazed at how smooth Ubuntu runs on such slow hardware. Thanks.

---

### Post by kojitsu on 2005-04-21
Oden, you have companionship in your battery monitor issues.  Mine is doing the same thing.  I am trying a multitude of things, but I am a newbie to Linux, thus I don't really know what I'm doing.  If I somehow come across a fix, I will let you know.

---

### Post by oden08 on 2005-04-22
Thanks for replying kojitsu.  I am trying some things too but haven't had any luck either.  I wonder if this would be fixed in Hoary but won't be able to find out until they ship it (I am still an unfortunate dial-up soul).

---

### Post by kojitsu on 2005-04-23
Ahaha, I feel your pain my friend, I too am suffering on dial up.  I believe I should request a copy of the newest version of Ubuntu, I've become rather attatched to it and would hate to go back on my "great distribution hunt."  *Shudders at thought of searching again*

---

### Post by mlna on 2005-05-06
Try adding acpi=force in file menu.lst
"kernel                  /boot/vmlinuz-2.6.8.1................. ro quit splash acpi=force"

---

