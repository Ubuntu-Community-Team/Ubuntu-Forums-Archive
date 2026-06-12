---
title: "AMD/ATI Open Source, just to understand something..."
date: 2011-01-10
forum: Hardware
---

### Post by Romu on 2011-01-10
Hi all,
I recently read on Phoronix that AMD has released the Open Source driver for the HD6k series.

To me this is pretty strange because my laptop runs a HD5650 graphic adapter and "out of the box" (so I guess with the radeon free driver), it is unable to run Compiz.

So, thanks to everyone who could explain in a simple way what's going on there.

Are there 2 free ATI drivers? If so what are their names? Which one is run by default on Ubuntu, which differences...

Thanks a lot.

---

### Post by EricJonsson on 2011-01-10
> Are there 2 free ATI drivers?
I guess there is, yeah. In places like [FONT=Courier New]xorg.conf[/FONT], ATI's proprietary driver is called [FONT=Courier New]fglrx[/FONT] while the free/open source version was simply (for applicable cards, of course) called [FONT=Courier New]radeon[/FONT]. On ATI machines, Ubuntu has installed the free driver per default, making them work out-of-the-box sans stuff like 3D acceleration and the like.

I've no idea what name this newly opened ATI-driver will take, or if it will be incorporated in the "official" F/OSS driver.

---

### Post by Romu on 2011-01-12
In the French Ubuntu documentation, I found there are, at least, 2 free drivers for the modern ATI graphic adapters: radeon and radeonhd.

But I don't know if the ATI own free driver is the radeonhd or a third one. I also don't know which ones do support 3D nor how to install them.

Any infos?

---

