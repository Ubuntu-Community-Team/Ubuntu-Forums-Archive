---
title: "&quot;Unknown&quot; Graphics card in the Settings - Ubuntu 12.04"
date: 2013-06-22
forum: Hardware
---

### Post by pmu on 2013-06-22
Hi,

New Ubuntu user here. Ubuntu 12.04 is great, but would be better if I could figure out how to get some more stuff working.

I have a Thinkpad T430, with Intel HD 4000 Graphics Card. No Nvidia "Optimus" Graphics. Just the Intel Graphics that came along with the Motherboard.

I googled and came across an article which in turn pointed to a [techlw article]("http://www.techlw.com/2012/08/install-latest-intel-gpu-drivers-in.html"). That techlw article stated that an xorg.conf file should be created. Tried that, rebooted fine, yet the graphics showed up as "unknown". So tried the steps given in the article:

```
step -1 sudo apt-add-repository ppa:glasen/intel-driver
step -2 sudo apt-get update
step -3 sudo apt-get install xserver-xorg-video-intel
```

At the third step it stated that the package cannot be installed due to two dependencies. I installed those, which basically involved removing about 35 packages and installing about 28 packages. It was my mistake to go ahead, because when I rebooted, got a blank screen. :(

So, I re installed Ubuntu 12.04. 

Is there an alternate way to get the Intel Graphics HD 4000 drivers apart from the article given above?

I dont want to go to 12.10 cause its not LTS though 12.10 has the drivers included.

Please help me on this one.

---

### Post by pmu on 2013-06-22
Yikes,

Searched on the forum, and about found a good article on the second page. Did that and now I have "Intel® Ivybridge Mobile" showing up in the Graphics Field of the Settings. My bad, I should have searched this before posting the answer. [Here is the link to the article]("http://ubuntuforums.org/showthread.php?t=2152065&highlight=intel+hd+4000").

I thought it would show Intel HD specifically, but that doesn't seem to be the case. 

Any further suggestions fellow Ubuntu Users?

---

### Post by CatKiller on 2013-06-22
What problem is it that you're having that you think installing a newer driver version will solve?

---

### Post by pmu on 2013-06-22
Hi Catkiller,

Thanks for replying.

I just want to ensure that the right drivers are there to avoid any crashes/issues. None as of now.

---

### Post by CatKiller on 2013-06-22
Just as a pointer, the way to avoid crashes and other issues isn't to install stuff from some random PPA, nor is it to rip out a whole bunch of packages at once.

If you know what you're doing, don't mind instability & want to help with testing then by all means experiment with PPAs. We could always use the help. Stability comes with choosing an LTS and leaving well enough alone.

Glad you're not actually having problems, anyway.

---

### Post by pmu on 2013-06-22
Hi,

Thanks for the advice.

---

### Post by grahammechanical on 2013-06-22
For the information of anyone who is interested, There are two kinds of video drivers for Ubuntu. One called Nouveau and it is open source and then there are the proprietary video drivers supplied by the maker of the graphic card. Both types are under continual development.

It is common for the details page of 12.04 to show "graphics unknown," especially if we are using the Nouveau video driver. The situation is a bit better if we use a proprietary video driver. The best result comes from using the latest version of Ubuntu (13.04). We may well see some information about the graphic card and the driver in the details page whatever the video driver. But do not expect the Details page to say anything about the Experience other than "Standard." That is the message since 12.04 was released until now.

We should not forget that Linux and its components are under continual development and usually be volunteer developers. The product is not yet finished by any means.

Regards.

---

### Post by pmu on 2013-06-23
Hi Graham,

Thank you for this update.

Due to certain requirements, I will have to stay on to Ubuntu 12.04. User Interface wise, I really loved 12.10 and there are a few things in 13.04 that dont work properly on my laptop, such as screen brightness resizing etc. Besides, 12.04 is stable and hence a good choice for primary OS to do work, hence the choice.

Thanks once again for providing details.

---

