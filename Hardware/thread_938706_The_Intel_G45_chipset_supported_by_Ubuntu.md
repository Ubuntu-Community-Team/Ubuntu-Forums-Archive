---
title: "The Intel G45 chipset supported by Ubuntu?"
date: 2008-10-05
forum: Hardware
---

### Post by BrigTSD on 2008-10-05
Can anyone confirm that the Intel G45 chipset is fully supported by Ubuntu? I am about to buy a Intel DG45ID motherboard but since it is quite new I suspect that the drivers are not available in Ubuntu 8.04. How about Ubuntu 8.10?

---

### Post by spoons on 2008-10-05
Hi there.

This what you are looking for?

[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=2](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=2)

---

### Post by Sef on 2008-10-05
> Can anyone confirm that the Intel G45 chipset is fully supported by Ubuntu? I am about to buy a Intel DG45ID motherboard but since it is quite new I suspect that the drivers are not available in Ubuntu 8.04. How about Ubuntu 8.10?

In short, 8.04 - no (you are correct.);  8.10 - they should be in.

Also you may want to look at this [thread]("http://ubuntuforums.org/showthread.php?t=889323").

---

### Post by BrigTSD on 2008-10-05
Thank you.

I also read at [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555") that they have been forced to disable the e1000e driver due to a serious bug.  This driver is necessary to enable the onboard LAN on DG45ID.

I think I will await the final release of Ubuntu 8.10 and see how it turns out before I buy this motherboard.

---

### Post by noisymime on 2008-10-07
You'll be right with the Intrepid 8.10 beta, although you won't have any ethernet. 

Alpha 6 still had a few graphical quirks with the 4500HD but the beta (or possibly the xserver updates since it came out) seemed to have fixed things up.

---

