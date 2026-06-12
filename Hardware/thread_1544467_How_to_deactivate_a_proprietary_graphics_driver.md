---
title: "How to deactivate a proprietary graphics driver?"
date: 2010-08-02
forum: Hardware
---

### Post by myosotis on 2010-08-02
Hi,

I just installed Ubuntu Studio 10.04 64-bit on my HP pavilion dv6 laptop. Things seem to work apart from the proprietary graphics driver. The graphics card is a ATI Mobility Radeon HD 5650. Before I installed the proprietary driver things looked fine, although I assume there is less support for 3D graphics. Would that be the case.

When rebooting after installing the driver the screen turns black before the login screen appears. I'm fairly new to Ubuntu so I have no idea how to sort this out without reinstalling completely.

My questions are:

1. Is there a way to deactivate the driver without reinstalling?

2. After reading on the forum it seems like others have problems with the proprietary ATI driver. What would be the disadvantages of running the generic driver? Or is there another solution?

---

### Post by myosotis on 2010-08-02
I found a thread that offered a solution to the first problem. I'm still trying to find a way to get the ati driver to work though.

---

### Post by brokenromeo on 2010-08-02
Which thread did you find...and did it work...from what I have read, I think your graphics card is so new, there isn't proper support yet...I have the HD4250 in mine and it works pretty well.

---

### Post by myosotis on 2010-08-02
This thread: [http://ubuntuforums.org/showthread.php?t=1430357&highlight=ati+fglrx+radeon+mobility&page=5](http://ubuntuforums.org/showthread.php?t=1430357&highlight=ati+fglrx+radeon+mobility&page=5)

I tried the first link provided by wistful.

---

### Post by P4man on 2010-08-02
The proprietary driver will offer better 3d performance. If you intend to play games, its something you want to get working. 

OTOH, the opensource ATI drivers work fairly well nowadays and especially for ubuntu studio, if you intend to use a low latency or RT kernel, the OSS driver is the one to use as the RT kernel doesnt work with the proprietary driver afaik.

---

### Post by myosotis on 2010-08-03
I'm not going to play games, but I might want to do 3D modelling eventually. For the time being I think I'll be ok.

But could the problem be the Ubuntu Studio settings? I think there was a question during install about the low latency, and I thing I chose not to use it, but is there  a way to find out? I chose Ubuntu Studio because I'm going to record music and edit video, but I assume I'm not going to need low latency. I could reinstall regular Ubuntu 64-bit I guess, if that's likely to make a difference.

---

### Post by P4man on 2010-08-03
open a terminal and type
```

uname -a
```

post the output here. 

Should you be using a low latency or rt kernel (which could indeed explain your problem), you can simply add a regular kernel, and select whatever kernel you want in grub during boot. You dont have to reinstall. But lets see which one you have first.

---

### Post by myosotis on 2010-08-03
I get the output:

Linux fennek 2.6.32-24-preempt #38-Ubuntu SMP PREEMPT Mon Jul 5 11:38:11 UTC 2010 x86_64 GNU/Linux

---

### Post by P4man on 2010-08-03
Preempt? Hadnt even heard of that yet. But it seems its not quite the vanilla kernel but a "soft rt kernel":

[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

I dont know if that one works with the proprietary drivers or not, but you can install kernels easily enough and find out if you can use those drivers with the vanilla kernel. Just install it through synaptic package manager. Search for linux-headers-2.6.34

You may have to run 

```
sudo update-grub
```

after that for the kernel to appear in grub boot menu.

---

### Post by myosotis on 2010-08-03
Hm. I can't find it in synaptic. The latest one I can find is 2.6.32.

---

### Post by P4man on 2010-08-03
Yeah you're right, sorry; 32 is the latest version in the official repo's. 

What matters here is not so much the version but the difference between the vanilla (generic) kernel and the preempt/ low latency / rt flavours. The proprietary drivers work with the vanilla kernel and the others is uncertain.  So just install the generic (headers and linux-image) and then you can try the proprietary drivers and see if that works.

---

### Post by myosotis on 2010-08-04
I managed to install and run the generic kernel, but the proprietary driver still doesn't work. Oh well. I'll wait and see. Thanks anyway, it was worth a try.

---

