---
title: "video card not detected"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2007-01-18
Hi folks,

I have a brand new HP laptop model nw8440. According to its system specifications, it has an ATI Mobility FireGL V5200 graphics engine with 256MB of VRAM.
My display has 15.4'' (wide screen) and supports a resolution of 1680x1050.

The maximum detected resolution is 1024x768, and there is something even worse: the video rendering seems to be done by the microprocessor  instead of the video card. When scrolling up and down the image gets cut and recreated on the fly.

Can I please ask for advice?
Thanks you in advance,
Adrian

---

### Post by belial6 on 2007-02-17
You need the fglrx driver for this card.
Install it by running this:
```
sudo apt-get install xorg-driver-fglrx
```

Then use aticonfig to update your xorg.conf file.
If you're using a basic setup and not dual monitors etc then you can just run:
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

For more complex setups see aticonfig help:
```
aticonfig --help
```

---

### Post by one_ro on 2007-02-19
Thanks very much, I solved it.
Love this forum, very helpful and friendly people.
Cheers,
Adrian

---

