---
title: "Looking for the latest video driver"
date: 2016-05-19
forum: Hardware
---

### Post by jacatone on 2016-05-19
I'm using Lubuntu 14.04 on an old 4600 Dell Dimension. I installed an equally old GeForce4 MX 440 AGP 8x video card. I'm looking for the latest video driver for this thing. Found the site listed below but don't know if I'm on the right track or not. Anyone know? Thanks.


[https://packages.debian.org/wheezy/nvidia-glx-legacy-96xx](https://packages.debian.org/wheezy/nvidia-glx-legacy-96xx)

---

### Post by Yellow Pasque on 2016-05-19
> **jacatone said:**
> don't know if I'm on the right track or not.

You're not. Nvidia's 96.xx proprietary driver isn't going to run on modern distros. The correct driver for your card ("nouveau") is installed by default. What exactly is the issue you have with it?

---

### Post by mörgæs on 2016-05-19
Here are [some ideas]("http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687") for tweaking.

---

### Post by jacatone on 2016-05-19
I notice some stuttering when I move an open window even though I've got 3 gigs of ram installed.

---

### Post by jacatone on 2016-05-21
When it says "Create xorg.conf.d/", is this a file or directly. The directions don't specify.

---

### Post by kalehrl on 2016-05-22
That's a directory.

---

### Post by jacatone on 2016-05-26
Found it made my system buggy. Had to remove it.

---

### Post by mörgæs on 2016-05-26
Then I suggest that you take a look at stronger graphics cards. They shouldn't cost much.

---

