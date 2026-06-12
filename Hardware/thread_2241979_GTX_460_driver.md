---
title: "GTX 460 driver"
date: 2014-08-29
forum: Hardware
---

### Post by gulmer on 2014-08-29
Just installed an older Geforce GTX 460 graphics card into my Ubuntu 14.04 64 bit computer. It's running on the 304. driver that the older card was using and it's working, just doesn't act like I think it should, not as fast or responsive. When I did a search for drivers, 3 different drivers showed up, 331.38 ,304.117, and the nouveau display driver. Which driver would be the best for the GTX 460?

---

### Post by Yellow Pasque on 2014-08-29
Since you have a Fermi card, I would use the latest stable driver offered by nvidia (343.13 as of this writing). It is conveniently packaged in this PPA: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by gulmer on 2014-08-30
First, what does having a Fermi card mean for my situation? Second, would just installing the 331.38 driver that's listed in the additional driver list work instead of trying the PPA route? Last time I changed drivers was on my wifes computer and we couldn't get back on to her desktop which makes me driver shy and leery, since. I have had success upgrading drivers in the past, then my wifes computer screw up. How can I be safe upgrading driver with my computer and how do you get your desktop back when all you get is black screen asking for your login info?

---

### Post by grahammechanical on 2014-08-30
We never know with proprietary video drivers. The way to get back depends on a few things.

Ubuntu 14.0 has a recovery mode in the Advanced Options sub-menu and the recovery menu has a Resume option that will/may load to a desktop using an open source video driver that Ubuntu 14.04 uses as a fall back video driver.

If we are getting to a desktop with a background image but no top panel or launcher, then we can try right clicking the desktop. If that brings up a menu, Select Change Desktop Background. That will load System Settings>Appearance. From there we can get to System Settings>Software and Updates>Additional Drivers tab. Then we can experiment with video drivers. and in my opinion it is all a bit of an experiment when using proprietary video drivers.

Regards.

---

### Post by Yellow Pasque on 2014-08-30
Having a Fermi card just means you can use the latest nvidia driver and don't have to worry about the "legacy" thing.  If you want to be absolutely safe, use the 331.xx driver.

---

### Post by gulmer on 2014-09-02
Installed the 331.xx driver, ubuntu running great, new graphics card w/this driver is a good match, thanks all for your help.

---

