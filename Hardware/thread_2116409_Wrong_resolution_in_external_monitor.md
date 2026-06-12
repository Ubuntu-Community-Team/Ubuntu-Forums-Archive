---
title: "Wrong resolution in external monitor"
date: 2013-02-15
forum: Hardware
---

### Post by Maharifu on 2013-02-15
Hi,

I have a TV, Hannspree HSG1115, which has a native resolution of 1920x1200.

However, when I connect it to my laptop (via VGA cable), it detects only 1920x1080, which makes it look stretched. I suspect the TV is sending wrong EDID information and so the correct resolution is not detected.

So my question is, can I force a 1920x1200 resolution? And if so, how?

I'm on ubuntu 12.10 64bit. My graphics car is a GeForce 8400M and I'm using NVIDIAs proprietary drivers (v304.43).

Thanks in advance.

---

### Post by SteveDee on 2013-02-16
> **Maharifu said:**
> ...my question is, can I force a 1920x1200 resolution?...

Try running xrandr to see which resolutions are available.
e.g. with external monitor connected, open terminal and type: xrandr

---

### Post by JohnDillinger43 on 2013-02-16
What options does it give you in the diplays window?  Typically it should give a range of options in a range of aspect ratios (though obviously the native resolution will look best).  Is the issue that it gives you a bunch of options but not 1900x1200?  Or that it doesn't give you any options other than the audodetected 1900x1080?

---

### Post by gordintoronto on 2013-02-16
Your problem is, "VGA cable." No HDMI on your laptop?

---

