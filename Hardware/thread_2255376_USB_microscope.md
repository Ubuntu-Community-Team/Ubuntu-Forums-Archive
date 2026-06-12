---
title: "USB microscope"
date: 2014-12-04
forum: Hardware
---

### Post by lordpuppet on 2014-12-04
Hi friends,

I just undusted a USB microscope I bought a few years ago. It used to work fine with Cheese.

But now everytime I plugg it, the lights go on and it isn't recognized by any software. Also, it doesn't let me do a **lsusb**. It just stops there until I remove it and then prints out the information.

Am i missing some packages?

---

### Post by mörgæs on 2014-12-04
> **lordpuppet said:**
> and then prints out the information.

Which information, lsusb? Please post.
Which microscope and which version of Buntu?

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by lordpuppet on 2014-12-04
As I've said, lsusb won't print out until I unplugg it. I'm using linux mint 16 mate.
Looks like it's working now:

> Z-Star Microelectronics Corp. Venus USB2.0 Camera

---

### Post by mörgæs on 2014-12-04
Good, please mark the thread 'solved'.

---

### Post by lordpuppet on 2014-12-04
Not yet solved. This behaviour its random, either way the thing doesn't work. Looking up in google I found out I need to compile gspca. I tried it but it just crashes with errors, apparently it doesn't work with my kernel version.

---

