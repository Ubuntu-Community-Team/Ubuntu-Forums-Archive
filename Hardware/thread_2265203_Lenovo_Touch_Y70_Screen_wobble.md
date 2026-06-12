---
title: "Lenovo Touch Y70 Screen wobble"
date: 2015-02-13
forum: Hardware
---

### Post by ck234 on 2015-02-13
Hello,
  I recently purchased a Lenovo Touch Y70 laptop.  My aim is to dual boot it.  I was able to successfully install Ubuntu 14.04 Desktop from a USB drive.

The major problem is that when running ubuntu the screen wobbles or vibrates.  It is just about usable, but obviously annoying.  The graphics card is Nvidia GFX.

Has anyone any suggestions to remedy this?  I have messed about a bit with nvidia drivers, but it hasn't helped yet.  I am struggling to install the latest proprietary nvidia drivers.  Perhaps there is an issue with the refresh rate with the touch screen, but I don't know.  The touch function on the screen does work fine.

There is no screen vibration when running under windows.

Thanks in advance for any suggestions.

---

### Post by ck234 on 2015-02-15
Update:  I tried a number of different distros from live CD to see which ones had the screen wobble.  All the ubuntu-based ones did (mint, trisquel, kubuntu etc), but the debian ones didn't.  I did think of installing debian, but ran into a few issues with the UEFI boot.

So, no further forward.

---

### Post by onvacs on 2015-02-26
I am having the same issue. The reason, as far as I can tell after about a night of experimentation, is related to how Debian will not configure hardware acceleration/rendering out of the box. I can run just about every "troublesome" distro, if I disable hardware rendering.

I would love to heard from you, or anyone else, who may have a solution to this.

---

### Post by Elmer Fudd on 2015-03-07
Been considering a Lenovo Y series touchscreen.  Has anyone had success with the Y50Touch? Does it have the same problem?

---

### Post by ck234 on 2015-03-28
No progress on this yet.  Screen still wobbles, but interestingly if I use an a second monitor, there is no wobble on that.

---

### Post by ck234 on 2015-04-10
Solved.

Installing the beta version of 15.04 solves the screen wobble problem.

---

