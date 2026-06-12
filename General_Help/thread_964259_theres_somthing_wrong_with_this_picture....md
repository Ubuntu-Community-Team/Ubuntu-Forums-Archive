---
title: "theres somthing wrong with this picture..."
date: 2008-10-30
forum: General Help
---

### Post by eival on 2008-10-30
[http://i33.tinypic.com/245y1w0.jpg](http://i33.tinypic.com/245y1w0.jpg)


thats ubuntu 8.10 freshly installed just an hour ago with the kernal security updates, nothing else added/installed/changed, and windows xp sp2 on the left with multiple apps installed and all updates excluding the SP3 upgrade

ive got both vm's installed on 10 gig base memory with 500mb ram and 32mb video each and i started them up at the same time.


i thought ubuntu were geared towards running better with limited resources than windows?

---

### Post by spiderbatdad on 2008-10-30
I don't recall any claims that Ubuntu runs on fewer resources. In fact running 3d rendering on the desktop, among other startup programs, can be slightly resource intensive. 1GB ram is much better than 500mb. Also Ubuntu will boot slower if you have hardware configuration issues that have not been compensated for via boot options or bios settings.

---

### Post by agathian on 2008-10-30
you might want to try booting without splash to see what is going on.

hit esc to go into grub menu, press "e" to edit, and delete "splash" and "quiet" off, and hit enter and b to boot.

It should show descriptive messages on what is going on.

By default ubuntu includes lot of packages to enhance user experience, if you want to run off limited resources you can run ubuntu server if it fits your requirement or there are plenty of other linux distros geared towards specific use models - check out distrowatch.com

---

### Post by b0b138 on 2008-10-31
Boot times in a vm is not an accurate speed test. On mine box, xp boots quicker in a vm than it did native. Intrepid in a vm is slow compared to hardy or gutsy. Im guessing this is due to vbox still being worked on for intrepid support. The 2.0.4 update added some support, but seems like it will need another update or 2

---

### Post by 3rdalbum on 2008-10-31
You're comparing the absolute latest version of Ubuntu with a seven-year-old version of Windows. No wonder there's a boot speed difference. Try putting Vista SP1 in the virtual machine and see what happens. If it's anything like real hardware, Ubuntu will load faster.

Or, better yet, install Windows 95 on the virtual machine and see how fast it boots up compared to XP.

Ubuntu isn't actually a lightweight Linux, either.

---

