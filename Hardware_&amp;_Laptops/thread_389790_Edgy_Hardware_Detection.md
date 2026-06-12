---
title: "Edgy Hardware Detection"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by doobydave on 2007-03-21
Anybody know how i can get edgy to detect my monitor. (and video card).

When i sudo dpkg-reconfigure xserver-xorg i just get generic.

Dapper is fine btw.

EDIT : My monitor is a iiyama vision master pro 510

---

### Post by mcduck on 2007-03-21
Only thing you have to care about is you video card. Your computer doesn't need to detect the monitor or even know if such thing exists at all. Just get your video card working and to use correct resolution & refresh rate and everything will work fine. (If nothing else then Radeon 9600-series cards work fine with fglrx drivers)

---

### Post by doobydave on 2007-03-21
I'm just a bit concerned that something that works in dapper no longer works in Edgy. Not really what I would call progress.

My video card is however a completely different story and i have given up trying to install fglrx for it as, frankly, it just doesn't work.

[https://launchpad.net/ubuntu/+source/xorg/+bug/89024](https://launchpad.net/ubuntu/+source/xorg/+bug/89024)

The monitor thing isn't a real problem as you say. I can get the resolution and refresh rates that i desire by changing xorg.conf

---

