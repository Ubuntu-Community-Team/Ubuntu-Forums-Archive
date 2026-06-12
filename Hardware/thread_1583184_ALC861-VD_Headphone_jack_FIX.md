---
title: "ALC861-VD Headphone jack FIX"
date: 2010-09-27
forum: Hardware
---

### Post by jamesa00789 on 2010-09-27
Hi there. After several months of pain and glory, which included messing up my ALSA settings a reinstall of Ubuntu 10.04 I have found a fix for solving the headphone jack issue using the ALC861-VD chipset. This thread is old, but wanted to share that it does work:

[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

Add "options snd-hda-intel model=dallas" to /etc/modprobe.d/alsa-base by:

```
sudo nano /etc/modprobe.d/alsa-base
```

Then reboot. I would post on the past topic but it is old and this bug still continues in Ubuntu 10.10! Please fix this.

Note: I do not have a Toshiba but a Packard Bell Easy Note and this still fixes this bug.

Thank you so much and I hope this solves a lot of issues. :)

---

### Post by jamesa00789 on 2010-12-27
I can say that this bug still HASN'T been fixed! Common Ubuntu dev's :(

---

### Post by squigles1 on 2011-08-24
> **jamesa00789 said:**
> Hi there. After several months of pain and glory, which included messing up my ALSA settings a reinstall of Ubuntu 10.04 I have found a fix for solving the headphone jack issue using the ALC861-VD chipset. This thread is old, but wanted to share that it does work:

[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

Add "options snd-hda-intel model=dallas" to /etc/modprobe.d/alsa-base by:

```
sudo nano /etc/modprobe.d/alsa-base
```Then reboot. I would post on the past topic but it is old and this bug still continues in Ubuntu 10.10! Please fix this.

Note: I do not have a Toshiba but a Packard Bell Easy Note and this still fixes this bug.

Thank you so much and I hope this solves a lot of issues. :)

How do I do this?  
I am having problems with headphone jack on a Packard Bell Ubuntu 11.4.
I opened the terminal entered the code sudo nano /etc/modprobe.d/alsa-base
Which done something and wrote options at the bottom of the terminal
I then tried entering options snd-hda-intel model=dalla
but nothing happened.

---

### Post by squigles1 on 2011-08-24
Sorted.
Followed instructions on another thread [QUOTE[]http://ubuntuforums.org/archive/index.php/t-1745051.html]("http://ubuntuforums.org/archive/index.php/t-1745051.html")[/QUOTE] To type sudo gedit   /etc/modprobe.d/alsa-base.conf in the terminal then added your code > options snd-hda-intel model=dallas as an extra line at the end
Thanks!

---

### Post by jamesa00789 on 2011-09-03
As of today in 11.04 this bug has still not been fixed.

---

