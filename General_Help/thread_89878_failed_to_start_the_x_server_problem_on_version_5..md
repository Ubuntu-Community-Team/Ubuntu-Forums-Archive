---
title: "failed to start the x server problem on version 5.10 using laptop"
date: 2005-11-13
forum: General Help
---

### Post by Geeke on 2005-11-13
Hello all I just got the live cd of version 5.10 when I try to load it using the live cd it starts to load then get this message Failed to start the X Server.

Here is a screen shot of the image maybe somebody can help me out here.


[IMG]http://img250.imageshack.us/img250/1320/img00408ra.jpg[/IMG]

I am not even touching anything when all that stuff comes up on the screen.

Laptop Specs
Model: Gateway 400SP Plus
CPU: Celeron 2.2ghz
Memory: 768mb
OS: Windows XP Home/with SP2
Graphics  Card: Intel(R) 82852/82855 GM/GME Graphics Controller


Can somebody tell me what my problem is or what I need to do to fix this?

Thanks to all that respond :KS

---

### Post by Qrk on 2005-11-13
type into the command prompt

sudo dpkg-reconfigure xserver-xorg

Most likely you need to try a different driver for your video card. try a few different ones out. Some will work some won't. I'd try "nv" or vesa. Vesa seems to run on anything.

---

### Post by Geeke on 2005-11-13
[QUOTE=Qrk]type into the command prompt

sudo dpkg-reconfigure xserver-xorg

Most likely you need to try a different driver for your video card. try a few different ones out. Some will work some won't. I'd try "nv" or vesa. Vesa seems to run on anything.[/QUOTE]


ok thanks :) going to go try it now.

---

### Post by Halibutt on 2007-07-11
> **Geeke said:**
> ok thanks :) going to go try it now.
Have the same problem on my HP nx8220. However, either the above solution does not work or I get something wrong (I'm a complete newbie, you know). After the error screen appears and two logs follow, I hit Alt+F2 and type sudo dpkg-reconfigure xserver-xorg, but it tells me there's no such command and nothing happens. Any ideas?
Cheers

---

