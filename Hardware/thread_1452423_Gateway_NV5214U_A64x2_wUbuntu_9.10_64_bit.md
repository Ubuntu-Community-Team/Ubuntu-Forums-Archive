---
title: "Gateway NV5214U A64x2 w/Ubuntu 9.10 64 bit"
date: 2010-04-11
forum: Hardware
---

### Post by ingramproductions on 2010-04-11
So far it was a really smooth install. Everything is working great after a few changes.
I had to add the the ATI/AMD proprietary FGLRX graphic driver from the Hardware Drivers tool. After that, all the desktop effects and 3d games work fine.
I did have problems with the wireless connection. It would connect, but disconnect after a few minutes. It would not reconnect unless I restarted the system. After some research, I found a solution:

[http://ubuntuforums.org/showthread.php?t=1374910]("http://ubuntuforums.org/showthread.php?t=1374910")

This is what got it working for me:
```
sudo apt-get install linux-backports-modules-karmic
```
and
```
sudo apt-get install linux-backports-modules-wireless-karmic-generic
```
I had to add the graphic drivers again after doing this, but it got the wireless working.

Sound and video seem to be doing great. No complaints on that or the wireless. I haven't tested out the webcam or media card reader yet, but I will update this when I do.

---

### Post by teamcoltra on 2010-05-07
I have an NV5214u as well...  Does your internal/external mic work? Mine does not.

---

### Post by ingramproductions on 2010-05-23
Yea, my microphone works.

---

### Post by ingramproductions on 2010-05-23
I've installed Ubuntu 10.04 Desktop 64 bit on this machine now, and it seems to be working much better than when I first installed 9.10. Everything worked great after the install. There was no need to install anything extra to get the wireless working like on 9.10. The only thing I noticed not working is the media card reader. I haven't attempted to get it going yet though.

---

### Post by ingramproductions on 2010-10-20
Did a fresh install of 10.10, and again, everything works great. Media card reader works too, it just doesn't mount media cards automatically.

---

