---
title: "linux kernel updates"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Andra on 2009-10-23
hello group,

Ubuntu 8.04, Gnome 2.22.3, Update Manager
For some days in Recommended updates there are kernel image and headers version 2.6.24-24.61. I didn't install them. Today in Important security updates there were kernel image and headers v.2.6.24-25.93 which I chose  to update, and again uncheck that one in Recommended updates. After update I have kernel 2.6.24-25-generic, and Update Manager still offering that 2.6.24-24.61. Is it normal? Now I do not want to install it at all - it's a lower revision!

---

### Post by markbuntu on 2009-10-23
Just so you know, reccomended updates are usually minor bug fixes etc that are not critical. For kernel updates many of them just add a few hardware driver fixes and other non-security related stuff and every update the changes the kernel number, like from -24.58 to -24.61. These will not change the kernel listing in grub.

Eventually these updates and some security updates and upstream fixes are rolled up into a new kernel and this will cause a change in the number like from -24 to -25. This will generate a new kernel and create a new kernel listing in your grub menu. 

If you want to keep the older -24 kernel up to date in case you might need it, you can get the updates. They will not effect the -25 kernel. it will also get update manger to stop bothering you.

---

### Post by Andra on 2009-10-25
Oh, thanks, now understand why so. :roll:

---

