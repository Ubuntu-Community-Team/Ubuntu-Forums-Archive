---
title: "How can I optimize ubuntu with my current hardware?Hello Ubuntu users. I run Ubuntu 1"
date: 2010-08-27
forum: Hardware
---

### Post by loooongcat:3 on 2010-08-27
Hello Ubuntu users. I run Ubuntu 10.04 in 64 bit. My current hardware specs are:

(2) Nvidia 8800 GTS
Asus Crosshair 1 
AMD Athlon X2 5200+
2GB DDR 3 Corshair ram

How can I utilize my hardware to it's full potential using Ubuntu?

Thanks for reading. I hope you can help.

---

### Post by warfacegod on 2010-08-28
Depends on what you want to do with it.

A good place to start is to turn off as much as possible in Startup Applications.

```
sudo apt-get install bum
```

An app that shuts off things that Startup Applications only makes you *think* are off, like bluetooth. Careful with this app. It can be dangerous.

Another thing to try is reducing your swapiness to a lower number like 20. You'll need to search the forum on how to do this, I don't recall off hand. (I don't use a swap at all and I have less RAM than you do.)

Another is to remove as many unused packages as you can with Synaptic. I've been able to get rid of over 800 MB without anything going wrong.

---

### Post by warfacegod on 2010-08-28
If, on the other hand, you want to push your hardware to see what it can do, play with Compiz.

A quick, dirty trick in this area is to install Chrome and start opening tabs. One of my fellow Admins. in the forum in my sig said he got 2 GB RAM use with just handful of open tabs. I read somewhere here that someone had 7 out of 8 GB full with only 20 tabs.

---

### Post by Fir3chi3f on 2010-08-28
Another thing you can do is remove some of the unused video drivers, likely not much of a speed increase, but it might boot a little faster and more disk space. 

System>Administrator>Synaptic Package Manager and do a quick search for 'xorg' and select 'completely remove' on any drivers you know, with certainty, you don't use.

For example, since you use an Nvidia card you can likely remove: xserver-xorg-video-intel and xserver-xorg-video-ati 

NOTE!::**I AM NOT responsible if this breaks your video! Please weigh the options and only proceed if you think it is worth the risk!**

Besides that, things start getting more difficult. After all the developers are trying to do this exact thing for everyone to realize the full potential of their hardware.

---

