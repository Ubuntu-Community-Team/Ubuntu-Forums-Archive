---
title: "HP Laptop w/ Nvida GPU, Running off battery =&gt; BUGS"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by sedd on 2007-08-19
Hi, 

I have an HP nw9440 with an Nvidia quadro 350M gpu. The hardware has always been a little bit flaky, but lately (since feisty) its been pretty smooth. I can even suspend, although X becomes way sluggish after waking up, so I can't really use it. 

Anyway, some time (I don't know when) this thing started happening. If I boot up before putting the power cable in (ie, running off battery) then the display has terrible bugs. Pixels in the wrong place. And its not a monitor thing, its in the framebuffer because when I take a screen shot the bad pixels are there. If I boot up with the power cable in, then take it out, everything is fine.

This thing only has an hour or so of battery, so its not THAT big of a deal. I'm just wondering if anyone else has noticed this.

If I needed to switch nvidia drivers, how would I do that using apt? I can compile my own (from nvidia), but I don't want to mess with debian's system for managing the kernel and it's modules. I don't really know how it works.

I attached a screen shot, just of the file browser (nautilus)

Thanks,
S.

---

### Post by tseliot on 2007-08-20
> **sedd said:**
> If I needed to switch nvidia drivers, how would I do that using apt? I can compile my own (from nvidia), but I don't want to mess with debian's system for managing the kernel and it's modules. I don't really know how it works.
Do you use Nvidia's proprietary driver already?

---

### Post by sedd on 2007-08-25
yes I'm already using nvidia's drivers. 

xorg.conf: Driver "nvidia"

---

### Post by tseliot on 2007-08-26
try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

