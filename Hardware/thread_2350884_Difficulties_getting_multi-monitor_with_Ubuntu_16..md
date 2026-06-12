---
title: "Difficulties getting multi-monitor with Ubuntu 16.04.1 and nVidia GeForce GTX 550 Ti"
date: 2017-01-28
forum: Hardware
---

### Post by carlos.rodrigues on 2017-01-28
Hello,

I'm having trouble getting multiple monitors (3 specifically)  working with my nVidia GeForce GTX 550 Ti card on Ubuntu 16.04.1. My current configuration is that I have 3 monitors connected via DVI: 2 via GPU and 1 integrated/onboard graphics.

I've done multiple installs and tried all available drivers (at least, from whatever is available after a vanilla installation). Those drivers include nVidia 304, 340 and 357, with 357 being entirely unstable, and the Nouveau driver which was installed/enabled by default. I should note, at best I was able to get the two monitors running from the nVidia card working, but while recognized and "enabled," the monitor connected to the iGFX stayed black and caused the mouse visibility to flicker.

Any thoughts on what I can do to get this configuration working? I'd be happy to post whatever details someone may need for better insight.

Thanks!

---

### Post by T.J. on 2017-01-29
Because the default Ubuntu installation is not tested for cases involving two different GPUs, you may have a few initial problems, especially if the integrated controller is a different brand or is an Nvidia card unsupported by the Nvidia driver.  These problems can be solved if you are willing to configure your displays manually.  Without more specific information, I cannot help.  Posting the listing from "lspci -vnn" as well as describing what display is connected to which card would be necessary.

This kind of problem is not confined to just Linux (Windows too), but it is rather rare. Not many people drive multi-displays with more than one discrete card where one is not slaved.

It can be done successfully.  I have configured an AMD and an Nvidia card in a single machine, for example.

---

### Post by carlos.rodrigues on 2017-01-31
> **T.J. said:**
> Because the default Ubuntu installation is not tested for cases involving two different GPUs, you may have a few initial problems, especially if the integrated controller is a different brand or is an Nvidia card unsupported by the Nvidia driver.  These problems can be solved if you are willing to configure your displays manually.  Without more specific information, I cannot help.  Posting the listing from "lspci -vnn" as well as describing what display is connected to which card would be necessary.

This kind of problem is not confined to just Linux (Windows too), but it is rather rare. Not many people drive multi-displays with more than one discrete card where one is not slaved.

It can be done successfully.  I have configured an AMD and an Nvidia card in a single machine, for example.
Thank you T.J.! I appreciate all the help you can give and will be more than happy to get you any info you need. I've attached the result of lspci -vnn (it doesn't appear to be saving or visible on my post, if not please see: [http://pastebin.com/raw/nwiZXwxQ](http://pastebin.com/raw/nwiZXwxQ))

What's the best way to describe which display is connected to which card? I have one monitor connected to "Display controller [0380]: Intel Corporation 2nd Generation" which is currently working as expected, and two monitors connected to "VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti]". One of the two monitors connected to the 550 Ti card is working as expected, and the other seems to be recognized within System Settings > Displays, but attempting to enable the monitor fails and is generally met with the following error (this error is also immediately raised on startup):

**    Could not switch the monitor configuration**
    could not set the configuration for CRTC 64

Sorry for the slow response. I'll try to be more responsive from here on out.

---

