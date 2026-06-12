---
title: "Image on TFT offset to the right by 2 or 3 pixels"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by bluesceada on 2006-07-07
Hi,
my laptop has a TFT with a 1024x768 resolution and a Trident Cyberblade i1 graphics adapter. Now I tried it with an older Knoppix (V3.4 from 2004-05-17) I still had laying around. Everything was fine with the TFT display. After that I installed Kubuntu. At the Installation the image on the tft was already offset to 2 or 3 pixels to the right.. so I have 2/3 lines of pixels missing at the right and 2/3 black lines at the left. I tried to fix it somehow with different Modelines (those from the old Knoppix) but they didnt work. I also tried around with the driver options, still doesn't work.
Now I think, that there is a bug in the newer Xorg trident drivers. I am downloading the newest knoppix at the moment to see if it's maybe some configuration problem of kubuntu.

Any ideas to fix this are welcome, thanks

---

### Post by bluesceada on 2006-07-07
Okay! I tried out Knoppix 5.0.1 .. the Problem doesn't exist there...
It is something specific to Ubuntu!
Now I just have to find out what it is ...

Any ideas are still welcome!

EDIT: I tried it with the newer knoppix 5.0.1 - and there it is working!

So: It is either a (k)ubuntu problem or the specific version of xorg (k)ubuntu is using,
--> I set everything which could affect it in the xorg.conf to what knoppix was using.. but no luck, so it seems ubuntu uses some other version of xorg ?
knoppix does use 7.0, but (k)ubuntu is also using 7.0 ...
maybe some minor differences, or other configurations ?

Can anyone tell me a way of fixing this? Please!

---

### Post by coffeecat on 2006-07-07
Edit: sorry - forgot that this was in the laptop forum, and posted a load of irrelevant stuff about desktop monitors.

---

### Post by bluesceada on 2006-07-08
too bad .. so no one can help me?
It works in knoppix! it really has to do with some specific stuff in kubuntu..

Maybe anyone can tell me how to update some of the X stuff to something newer, maybe more "testing" or "unsupported". I'd just want to try it out at least.
Thanks in advance!

I reported a bug:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-trident/+bug/52321](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-trident/+bug/52321)

It seems to work with the vesa driver! But knoppix is definately using the trident driver (I checked the Xorg.0.log and the xorg.conf of knoppix).

---

### Post by bluesceada on 2006-07-11
Nobody can help ?
I even tried edgy and it's also like that there...

---

### Post by steve.carren on 2006-09-06
I have had the same problem. Other distributions seem to work, but not Ubuntu. No tweaks seem to help. If I ever figure it out, I will post.

---

