---
title: "A8JS Laptop"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by Biscuits N' Gravy on 2007-04-21
I just installed Ubuntu 7.04 on my Asus A8JS laptop and I've notcied that it gives me trouble with the Geforce Go 7700 video card.  Is there any way I can get full performance from my video card?

I've read the other threads about the laptop but I'm such a noob I really can't comprehend what's being said.  Also, is there any other pieces of hardware I should have to get working as well?

Thank You,
Biscuits

---

### Post by hardyn on 2007-04-21
Using the nvidia-glx-new driver will get you as much video performance as you can.
I would not spend alot of time trying to get the card reader working, unless you really really need it.
Everything else should work out of the box, although some has had problems with the 3419 wireless.

good luck.

---

### Post by Biscuits N' Gravy on 2007-04-21
> **hardyn said:**
> Using the nvidia-glx-new driver will get you as much video performance as you can.
I would not spend alot of time trying to get the card reader working, unless you really really need it.
Everything else should work out of the box, although some has had problems with the 3419 wireless.

good luck.

Could you help me out with that..... I'm very new to Ubuntu.

The wireless works great.  The card reader doesn't matter because I don't use it anyway.

Thanks

---

### Post by hardyn on 2007-04-21
it should not be much more than selecting it the restriced softwar manager, which should be under settings->administration.

Im not on my ubuntu box right now, so that is the best i can do this very second.
have a seach if you cannot find it... pretty much every install and setup question has been asked... twice.

good luck.

---

### Post by Biscuits N' Gravy on 2007-04-21
I did it and I get to enable the wiggle windows but I get the same 1024x768 resolution but with 50hz refresh rate instead of 60.  Oh well, I guess drivers will get updated over time? 8-)

---

### Post by hardyn on 2007-04-22
Use:

sudo nvidia-settings

the gnome resolution doesn't seem to report properly with the nvidia binary driver...  im running 1680x1050 @ 60hz

---

### Post by Biscuits N' Gravy on 2007-04-22
After a little searching and using the "Synaptic Package Manager" coupled with the terminal window I was able to get the 1440x900 resolution I was looking for.

Thank you for the help,
Biscuits

---

### Post by veratyr on 2007-04-23
When using the restricted driver manager to install the nvidia driver with my a8js it tries to install nvidia-glx rather than nvidia-glx-new. Make sure you are using nvidia-glx-new.

---

### Post by Biscuits N' Gravy on 2007-04-23
Yeah I didn't have the new glx and didn't know it until I went to the synaptic package manager and clicked on not installed and it showed it wasn't installed.

Do you have functionality with your scroll on the touchpad?  I can't figure out how to make the scroll function work.

---

### Post by Biscuits N' Gravy on 2007-04-23
Also, what about where I can double-click the scroll bar and hold it and make the scroll bar go up and down.

Thanks ahead of time

---

### Post by veratyr on 2007-04-24
look here.

[http://ubuntuforums.org/showthread.php?t=328788&highlight=asus+a8js](http://ubuntuforums.org/showthread.php?t=328788&highlight=asus+a8js)

---

