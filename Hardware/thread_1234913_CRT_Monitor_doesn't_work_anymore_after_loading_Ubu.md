---
title: "CRT Monitor doesn't work anymore after loading Ubuntu?!"
date: 2009-08-08
forum: Hardware
---

### Post by mikgerdan1991 on 2009-08-08
I downloaded and burned the CD, and I was really excited to get Ubuntu onto my computer, because I've used Windows all my life. I booted from the CD (It's version 9.04) and I selected something like 'boot from the liveCD' or whatever the option is to use it from the CD without installing it. After the Ubuntu loading screen, and it was just about to load, my monitor (20" CRT Gateway) made the demagnetizing noise, like it makes when you turn it on. I figured it was no big deal, and it was just adjusting to the new OS. I saw the Ubuntu desktop, and I immediately saw that the screen was set for some weird dimension. Probably for a wide screen or something...Within a couple minutes, my monitor shut off. And stayed off...
I've searched the forums, and could not find this problem. Does Ubuntu 9.04 use an unusually high refresh rate or screen resolution that could have blown my monitor? That's what I'd like to know. 
And how to get it back on, of course...

---

### Post by cariboo on 2009-08-08
Try running the Live CD in safe graphics mode, your monitor is not being detected properly. To use safe graphics mode press Alt-F4 at the menu screen and select the safe graphics mode option. Then select whatever option you want from the Live CD menu.

---

### Post by mikgerdan1991 on 2009-08-08
Thanks for the reply.

But no, no, you misunderstood me. My monitor was detected fine. But once it booted, it looked like the very left and right sides of the monitor weren't there, as if it was set for a wide screen resolution.
But the main point is, my monitor doesn't turn on AT ALL anymore. Isn't detected by Windows. Doesn't turn on. Ever since I tried to boot Ubuntu from that CD...

---

### Post by mikgerdan1991 on 2009-08-09
I guess my question is, does that widescreen resolution do anything to my regular CRT monitor?

---

### Post by Narada on 2009-08-09
You may have fried it with misconfigured modelines in your xorg.conf if it's not working at all. :/

---

### Post by mikgerdan1991 on 2009-08-09
That's all I wanted to know. 
I mean, how can that happen though? And what caused it?
I never thought software could do damage to actual things, other than data, etc. Now I've seen everything...

---

### Post by mikgerdan1991 on 2009-08-11
Or has anyone ever heard of this before...?

---

