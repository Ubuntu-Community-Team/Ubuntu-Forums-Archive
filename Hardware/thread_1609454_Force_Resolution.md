---
title: "Force Resolution"
date: 2010-10-30
forum: Hardware
---

### Post by bonfire89 on 2010-10-30
Hi there,

I have a Dell Latitude E6410 with Intel HD graphics and I am not able to select 1440x900 as a resolution for my monitor.

In the past the problem with this particular monitor has been that the aspect ratio gets recognized wrong and playing with the horizontal/vertical refresh seems to help, but I am not having luck with this particular machine and with ubuntu 10.10.

How can I force 1440x900?


Thank you




Edit:

I just had some success but I have no idea really what I did


I ran

cvt 1440 900

then used info from there to then run

xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

then I ran

xrandr --addmode VGA1 1440x900_60.00


and from there I was able to enable the resolution



but... I think I need to add this to my xorg.conf now

I'm scared to ever restart this machine again. lol



Edit: from there I did some guessing and used some of that info and got a xorg.conf file working.

---

