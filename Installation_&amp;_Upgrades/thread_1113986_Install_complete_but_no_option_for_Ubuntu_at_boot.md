---
title: "Install complete but no option for Ubuntu at boot?"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by soomro on 2009-04-02
As the title says i installed Ubuntu as guided and i was done when i restarted i did not have the option of Ubuntu i only had options for my Windows7 and Windows XP how do i make it appear there as a selection? or if it said that i can run it alongside windows why it ain't working?

thanks

---

### Post by dandnsmith on 2009-04-02
Did you install ubuntu to the HDD, or did you do an install under wubi?

---

### Post by soomro on 2009-04-03
> **dandnsmith said:**
> Did you install ubuntu to the HDD, or did you do an install under wubi?

I installed it to my hard drive and what is wubi?

probably i have two hard drives i installed it on my first hard drive it happened the same with Kubuntu as well...

---

### Post by dandnsmith on 2009-04-03
You are not getting the grub bootloader installed to the hard disk which is being booted, so the same old stuff is what you see.

You need to include more detail about what physical hard disks you have, which you installed to, which ubuntu you installed, and which installer.

wubi can organise an ubuntu installation within Windows filesystem, which can be booted as an alternative to Windows (using the Windows boot menu).

---

### Post by soomro on 2009-04-03
Well i got the GRUB started and i can run it well. So thanks a lot.

---

