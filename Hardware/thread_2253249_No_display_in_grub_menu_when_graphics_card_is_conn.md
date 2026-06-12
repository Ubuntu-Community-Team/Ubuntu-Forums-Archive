---
title: "No display in grub menu when graphics card is connected."
date: 2014-11-18
forum: Hardware
---

### Post by simon66 on 2014-11-18
Hello Forums,

I have an nvidia gtx 460 in my pc. I've dual booted windows 8 and Ubuntu with no issue, until I connect the graphics card. When the graphics card is connected, My monitor remains blank when the PC starts. There is no display in the grub menu. The power light on the monitor comes on, so it thinks it's getting something, but nothing appears. If I disconnect the graphics card entierly, and operate only from onboard graphics, everything is flawless, but I'd like a second monitor, so I'll need a graphics card!

I don't know what information I need to give to help solve the problem, so I can post whatever is needed as it's requested.

---

### Post by grahammechanical on 2014-11-18
You have what is called hybrid graphics. I have no experience with hybrid graphics but the problem could be caused by not having a video driver for the Nvidia adapter. Intel video drivers come as Linux kernel modules. This is the best that I can offer.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

[http://www.webupd8.org/2014/09/recent-update-broke-ubuntu-desktop-on.html](http://www.webupd8.org/2014/09/recent-update-broke-ubuntu-desktop-on.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

Regards.

---

### Post by simon66 on 2014-11-18
I'm using a desktop PC, so I don't _think_ it's hybrid graphics, at least in the sense that it didn't come that way. The gfx card was manually added by myself.

---

