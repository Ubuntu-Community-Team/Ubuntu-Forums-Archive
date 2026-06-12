---
title: "Inspiron e1505 (6400) keyboard issue"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by ReverendJT on 2006-11-04
I just installed Ubuntu Edgy on my Dell e1505 (also known as the 6400) laptop and I'm having an issue with the keyboard Fn key. Both in Windows and any time before X starts I can use the Fn key in conjunction with the arrow keys to change the brightness of my LCD screen. Once X starts I lose this ability. The other Fn combinations seem to work alright though such as Fn+PageUp to increase the volume. Any help that could be offered would be greatly appreciated. I've attached a copy of my xorg.conf file.

Thanks.

---

### Post by thila on 2006-11-04
I have the same problem, I was going blind - I was even thinking of going back to XP.But the dirty work-around was I boot with  XP, adjust the brightness, which is then reflected when I reboot for Ubuntu. Not elegant, but works. I am lucky to have XP (:)


Does the Wifi and DVD write work for you?

---

### Post by ReverendJT on 2006-11-05
Yeah, I'm aware of such a work around but I really shouldn't have to do that to adjust the brightness :-(. I don't have a dvd writer but my wireless is working just fine. Its the Intel wireless card as opposed to the broadcom which I've heard gives some people difficulties.

---

### Post by lucads on 2006-11-13
I'm experiencing the same bug, but only after i upgraded my Inspiron 6400 bios from version A06 to version A09; in summary:

OK with ubuntu Dapper + Inspiron 6400 bios A06 
OK with ubuntu Edgy + Inspiron 6400 bios A06
BUGGED with ubuntu Edgy + Inspiron 6400 bios A09

Any proper solution to the bug?

---

### Post by lucads on 2006-11-20
this is the xorg.conf file i'm currently using both before (without kb issue) and after bios update (kb issue i'm currently experiencing).

---

