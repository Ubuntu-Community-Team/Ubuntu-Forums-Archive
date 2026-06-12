---
title: "HP 8510w laptop freeze with fresh 8.10 install"
date: 2008-10-31
forum: Hardware
---

### Post by Steeljaw on 2008-10-31
My HP 8510w laptop freezes after logging in to my freshly installed 8.10 in both i386 and amd64 variants. It boots up fine on a USB-stick and the live system works for at least 30 minutes. When I decide to install it to HD, the installation goes well. 

When I boot from HD and log in to the system it comes to a complete halt about 1-3 minutes after logging in (lit screen, progress bars and clock stopped, no response from mouse & kbd). I couldn't find any obvious errors in the logs on the HD after booting into the live USB again.

I swapped back the drive with my working 8.04 for now, but would really like 8.10 to work.

The 8510w has a nvidia quadro go 570m graphics adapter and intel 4965agn. I have a feeling it could be one of those messing it up. How would I go about to find out which one?

---

### Post by Astinsan on 2008-11-04
From what you said it sounds like a power throttle problem. Try keeping the system busy by moving the mouse or playing a internet radio station. My HP nvidia gpu/chipset is having issues with the new kernel too. But I think my problem has to do with another part of the nvidia curse. Mine locks up at the bootsplash. If I hit the power button it will load up all the way... its wacked. This issue is documented everywhere and we are not the only people having trouble with nvidia based laptops. I would expect it to be fixed soon. 

Lucky I imaged my drive before going into the 8.10. LTS will eventually get all the patches from 8.10 when they become stable. So I am not worried.

---

### Post by christopheclc on 2008-11-16
Hi,

The problem is actually your Intel 4965 agn wireless chipset, it was a known bug at release-time.  Please see the Ubuntu 8.10 Release Notes: [http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810"), it also tells you the package to install in order to fix this problem, which is: linux-backports-modules-intrepid.

I have an HP Pavillion dv9500t laptop with the exact same chipset, and I had the exact same problem.  Installing the recommended package seemed to fix the problem.  However, I noticed last night my laptop froze again while I was asleep.  I checked the syslog, and the only messages I saw before the crash were related to the wireless driver.  Nothing that looked suspicious, though, just a "mode change" from 7 to 6.  Either way, I can definitely tell you that installing the package they recommend will at the very least greatly reduce the freezes, if not make them go away.  My problem may have been completely unrelated to the wireless driver.

Good luck!

Christophe

---

