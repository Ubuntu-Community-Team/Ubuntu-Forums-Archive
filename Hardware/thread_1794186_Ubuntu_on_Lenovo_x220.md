---
title: "Ubuntu on Lenovo x220"
date: 2011-06-30
forum: Hardware
---

### Post by pederbruusgaard on 2011-06-30
I'm all new to Ubuntu, and considering the Lenovo x220, which they say is Ubuntu Ready. I know it's possible to install it later, get most/all things working, but I'm wondering how seamless it will turn out. I sort of don't really want to see Windows at all if I don't have to. Can I do automatic booting to Ubuntu, for example? As you might understand, I'm not an experienced Linux-er, but I'm eager to learn.
So, do I need to be a computer scientist to get Ubuntu to work smoothly on a Lenovo x220?

Thanks!

---

### Post by StartedTheFire on 2011-07-07
I have the same question, basically; I was about to make a new thread. Although I know a little something about linux after having run it for a year or so.

I'm just concerned about support for the touch screen and whether or not features like pressure sensitivity and multitouch will carry over.

Also to the OP, ubuntu isn't difficult to install at all- I'm sure it'll install fine, I'm only worried about the touch screen. It's packaged to be almost as easy to use as windows, without making any sacrifices whatsoever in the area of efficiency, speed, or openness. I love this OS.

---

### Post by nom_nom on 2011-07-12
I have recently purchased an x220 and was running Ubuntu 11.04. All in all, it worked really well. Most everything worked right out of the box with two main exceptions. One, not a huge deal, the other pretty nasty.

First, if you are running the i7 model with USB 3.0, you cannot get suspend working with the USB 3.0 controller active. I keep USB 3.0 off so my computer will suspend and turn it on manually when I want to connect a USB 3.0 device to the computer and turn it off when I disconnect the device. I don't really use the USB 3.0 too much so it hasn't been a huge issue for me.

Second, there is an issue with X server crashing. X server is the program that most of the other GUI elements run on top of. This causes your computer to be rendered inoperable. From what I have been able to gather it is a bug in kernel 2.6.38. You can manually update to kernel 2.6.39 and, from what I understand, this solves the problem.

Since Ubuntu is not hosting any repositories with kernel 2.6.39 I opted to install a different distribution, namely ArchLinux, until Canonical releases the beta for 11.10 with the new version of the kernel, which is due for release in September with the release version of 11.10 due for release in October.

For the novice user, I would highly recommend waiting 2-3 months and installing Ubuntu 11.10. Ubuntu is a really great distribution for novices and experts alike. And the Thinkpad x220 is a really great computer, I love mine! Even more than my old macbook (which had linux installed) that was stolen.

[https://help.ubuntu.com/community/X220](https://help.ubuntu.com/community/X220)
[http://ubuntuforums.org/showthread.php?t=1772937](http://ubuntuforums.org/showthread.php?t=1772937)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795407](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795407)

---

### Post by manybodycpa on 2011-07-13
Hi!

I have been running Natty (11.04) on an X220 with an i5 processor for three months now. I can confirm regular X-windows freezes using the 2.6.38 kernel. Switching to 2.6.39 via PPA at first resolved this issue, but a couple of other problems have come up recently:

1. Suspend or resume from suspend lead to regular crashes (including kernel panics, irresponsive x-server etc). This is much worse when an external display is attached, but also occurs without that (PCH error, reported by other users). No such problems occurred with 2.6.38.

2. The latest updated intel graphics drivers (also from PPA) do not allow any mpeg playback (mplayer has only sound, and freezes the whole system after a while). A couple of weeks ago, things were working fine. There are also issues with ghost images when switching desktops.

3. There is a minor bug with timeout of usb devices when running on battery.

4. Charge thresholds are not fully working within tp_smapi.

I like my X220, but given the Linux certificate from Lenovo, there are a few too many bugs for my liking. 

Best,

Martin

---

### Post by nom_nom on 2011-07-16
I recently reinstalled Ubuntu 11.04 on my x220 and haven't had any x crashes with the kernel 2.38.10 patch with continuous running over the past two days. I'd say the problem appears to have been resolved.

---

### Post by manybodycpa on 2011-07-17
Hi nom_nom,

Thanks for your info - however, when I first go my X220 it was running
fine for a week, but then freezes started to happen. Maybe this also
depends on usage - I use to switch through desktops very frequently,
which may cause problems with the graphics.

Anyway, let us know if you remain freeze-free.

Best,

Martin

---

### Post by umerlone on 2011-08-22
Hi, I just received a Thinkpad X220, i5-2410M CPU @ 2.30 with 8 Giga
I installed Ubuntu 10.04 as I was not very happy about 11.04.
Everything seems ok and I am really not an expert on Ubuntu.

I cannot have a screen resolution larger than 1024x768. Can anybody suggest me how to obtain a better resolution? Actually this is the only one I can obtain according to xrandr.

Thanks a lot

Ugo

---

