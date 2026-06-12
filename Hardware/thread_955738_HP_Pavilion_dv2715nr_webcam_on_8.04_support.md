---
title: "HP Pavilion dv2715nr webcam on 8.04 support?"
date: 2008-10-22
forum: Hardware
---

### Post by tbar3 on 2008-10-22
Hello all... relatively new to ubuntu here... (tried it out a while ago, and went back to windows... new laptop had Vista... it crashed, so Ubuntu comes back into play) :)

at any rate, i can't seem to get my webcam working.

running
```
lsusb
```
i get the following line:
```
Bus 003 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd
```
per [this link]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#webcam"), i've found that the 04f2:b015 is fully supported, but makes no note about the b016... is it not supported? is there no work around? any help would be appreciated. (this isn't a deal breaker for ubuntu for me, but would be nice if it worked...)

TIA,
TBare

---

### Post by tbar3 on 2008-10-22
well, apparently the webcam IS supported, and working... at least in Ekiga..  (read a post about the app, so i thought i'd try it out. works)...

but i'm getting errors when using camorama

```

Could not connect to the video device (/dev/video0). Please check the connection.

```

any thoughts on this?

---

### Post by brettnak on 2008-11-04
I have the same problem, and the same webcam.

I downloaded & compiled linux-uvc from their svn, and still no go.

Thanks,
Brett

---

