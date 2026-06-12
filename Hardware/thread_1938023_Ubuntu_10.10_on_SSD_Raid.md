---
title: "Ubuntu 10.10 on SSD Raid"
date: 2012-03-08
forum: Hardware
---

### Post by siersmak on 2012-03-08
Hello,

I am considering buying a laptop that has 2x128 GB Raid 0 SSD.  This one:  [http://www.buy.com/prod/sony-vaio-r-vpcsa45gx-bi-s-series-13-3-notebook-pc-jet-black/228350864.html](http://www.buy.com/prod/sony-vaio-r-vpcsa45gx-bi-s-series-13-3-notebook-pc-jet-black/228350864.html)

I very much want to put Ubuntu 10.10 on it, specifically so that I can run the old Gnome desktop.  That's a requirement for the user.  

I'm worried that I won't be able to install 10.10 on this hardware.  Am I crazy?  Should I stick to a standard SATA drive?

Thanks

---

### Post by Grenage on 2012-03-09
While there are subtle differences, it's just an SATA hard drive.  Now that there is kernel TRIM support, with a few tweaks, there is no reason not to use one.

I type this on an 11.10 SSD build.

---

### Post by siersmak on 2012-03-09
I agree and understand that the latest versions of linux can run on SSD Raid but my concern is that the **10.10** installer won't be able to recognize the hardware.

---

### Post by Grenage on 2012-03-09
As far as I can recall, 10.10 had TRIM support out of the box; others may correct me.  Regarding detection, I would expect you to have no problems.

---

### Post by siersmak on 2012-03-15
Indeed, Ubuntu 10.10 didn't have a problem with the SSD Raid in this laptop.  I've struggled to get other aspects of it working (wifi, sandybridge/radeon, touchpad...) but those are for other threads...

Thanks

---

