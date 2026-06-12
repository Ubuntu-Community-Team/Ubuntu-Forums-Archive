---
title: "Flickering on Radeon X 1250"
date: 2009-04-14
forum: Hardware
---

### Post by rajeev_n on 2009-04-14
When I run Jaunty Jackalope on my laptop (Compaq 6715b /Radeon X1250) the screen flickers very often and it is pretty unpleasant.

Do I need to install proprietary ATI drivers ?

Thanks in advance 

Rajeev

---

### Post by 0vermind on 2009-04-15
I am having the same problem and I have been trying to find a solution all day.

From what I have heard, there are no proprietary drivers for the ATI Radeon X1250 in Jaunty and there **NEVER** will be. At least that's what I was told, please someone correct me if I am wrong. (More information is located at [this topic.]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7080553"))

So I think that Ubuntu 8.10 is the last distro that will work with the Radeon X1250 without having problems? That's what I have come to the conclusion of. I would like to hear from a more experience user on this though, I always have problems with the drivers.


-Michael

---

### Post by Darent on 2009-04-30
Same problem in x1300... unninstall al fglrx and install the free drivers. xserver-xorg-video-ati and xserver-xorg-video-radeon

---

### Post by StuartN on 2009-04-30
> **0vermind said:**
> From what I have heard, there are no proprietary drivers for the ATI Radeon X1250 in Jaunty and there **NEVER** will be. At least that's what I was told, please someone correct me if I am wrong.

This is what the ATI release notes say:
> AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above. [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

However, I think that AMD are passing some of the proprietary code into the open source drivers, so the open source drivers are likely to improve over time.

---

