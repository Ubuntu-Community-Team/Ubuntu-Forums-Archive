---
title: "No card information in Nvidia X Server Settings"
date: 2015-08-29
forum: Hardware
---

### Post by shai_hulud2 on 2015-08-29
Hello,

I'm completely new to Ubuntu and this was preinstalled on a new computer. 

I have an Nvidia GTX 960 installed and am trying to setup dual monitors. The primary monitor is connected to the graphics card using a Displayport cable, the second is daisy chained. Right now, both monitors are showing the same screen.  I have uploaded to the latest Nvidia driver, 346.82 updates from additional drivers. 

The card is not showing in About this computer.  Also when I bring up Nvidia X Server Settings, there is no information whatsoever.  I assume this means Ubuntu is not recognizing the card?  Does something need to be changed in BIOS?
Any help is appreciated. I'm quite lost. 

Thanks,

---

### Post by blm-ubunet on 2015-08-29
According to the nVidia driver readme/supported products info you need:
349.16 short-lived branch or
352.41 long-lived branch

You get one of these from adding another ppa.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by shai_hulud2 on 2015-08-29
More information, after switching to the defaul driver, then back to the Nvdia driver and reinstalling the graphics card is now showing in the about this computer.  However, the right display, the one daisy chained stopped displaying completely, and the left display is flickering on and off every few seconds.  Adjusting the resolution to native seemed to help as the flickering has stopped but the right monitor is still showing no input when daisy chained or when connected directly to the card with a second display port cable.

---

### Post by shai_hulud2 on 2015-08-29
> **blm-ubunet said:**
> According to the nVidia driver readme/supported products info you need:
349.16 short-lived branch or
352.41 long-lived branch

You get one of these from adding another ppa.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Awesome, that seems to have done it. 

Thank you.

---

