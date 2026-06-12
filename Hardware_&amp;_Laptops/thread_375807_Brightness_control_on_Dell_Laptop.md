---
title: "Brightness control on Dell Laptop"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by Loonux on 2007-03-04
Im using kubuntu 6.10 and the Fn/Brightness key combinations do not work.

Is there anything i can do to fix this? The video card is an ati radeon X1400 256mb chipset if thats useful?

thanks

---

### Post by spacebetween on 2007-03-05
I am having the same problem running the latest Edgy with a Compaq Presario V2000 running ATI Radeon Xpress 200M (don't make fun of me). 

I've scoured the net and come up with nothing... does anyone have a solution?

---

### Post by spacebetween on 2007-03-05
bump

---

### Post by sstakes1 on 2007-03-12
I can't find the original post.But the following fix works for me.

Blacklist the video module in /etc/modprobe.d/blacklist. 
If you're unsure how, there are other lines in the file that may blacklist other modules. You would have to add a similar line blacklisting video.

HTH

---

