---
title: "DRI with ATI Rage Mobility = Hopeless?"
date: 2004-12-12
forum: Hardware &amp; Laptops
---

### Post by Arbiter on 2004-12-12
Hi all,

I've been trying to get DRI working properly with my ATI Rage Mobility chip in Ubuntu (warty).  I've tried several methods and none have yielded results.  I want to be able to get a somewhat useable framrerate with OpenGL.  I'm using a Sony Vaio PCG-FXA32 Mobile Duron laptop.  The utility 'lspci' gives me this result...

```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
``` 

I am using Ubuntu (warty warthog) with XFree86.  Like I said, several attempts at doing this have failed miserably.  Is this hopeless at this point?

---

### Post by kdavison007 on 2004-12-17
Wish I could help, but I have the exact same question you do.  I'm use an HP Pavilion ZE5470us that has the ATI Mobility card.  Mine is actually a Radeon, but I can't seem to even find a driver for it.

---

### Post by abe1999 on 2004-12-17
try this:

sudo gedit /etc/X11/XF86Config-4 

scroll down to Section "Screen"

Change DefaultDepth to 16. Restart and it should all be good 

 :smile:

---

