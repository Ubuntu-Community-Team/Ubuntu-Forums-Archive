---
title: "Elantech touchpad not detected. Where report bug???"
date: 2011-11-02
forum: Hardware
---

### Post by josvanr on 2011-11-02
Hi I have a samsung sf310 with elantech touchpad. It is not detected on kubuntu 11.04 , and on 11.10 even the buttons don't work. I tried to report a bug but I honestly cant find out where to do this. Any suggestions?

josvanr

---

### Post by ld114 on 2011-11-02
Hi josvanr

The elantech touchpad has been an issue in the kernel for a while. I have a Samsung netbook and the touchpad was recognized as a psmouse. I eventually found this patch which worked on 11.04. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904/comments/64)

You might try it. Have you got the Samsung tools from the Voria ppa (sudo add-apt-repository ppa:voria/ppa)? These tools enable you to switch the touchpad on and off. Might be of some use.

I notice you have tried Kubuntu 11.10 and the touchpad doesn't work - my touch pad is recognized properly in Ubuntu 11.10 so maybe it has a slightly more recent kernel version than Kubuntu 11.10. You might try an Ubuntu live disk for 11.10 and see whether there is any difference?

Hope this helps - I know it is very irritating when the touchpad doesn't work properly. 

ld114

---

### Post by josvanr on 2011-11-02
I'm not shure I want to dive in to comiling kernels, but as I read your post I was downloading ubuntu 11.10 already! Hope it works...

---

