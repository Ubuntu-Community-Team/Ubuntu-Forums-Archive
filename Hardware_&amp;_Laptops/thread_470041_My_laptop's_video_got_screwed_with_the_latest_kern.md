---
title: "My laptop's video got screwed with the latest kernel!"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by joe.turion64x2 on 2007-06-10
Hello everybody.

Until this morning I was enjoying a wonderful Ubuntu 7.04 system. Even Beryl was working nice with my ATI card, the volume shortcuts, everything. However I realized there was an update available, a new kernel  2.6.20-16 so I installed it (it is not the first time I update the kernel in Ubuntu). The problem here is that when I boot using this new kernel everything shows fine until I log in, after that the screen becomes an unrecognisable set of colors in which I can do nothing. I am pretty sure the problem is somewhere with the restricted ATI drivers, and perhaps X server, and maybe Beryl itself but don't find a method to update them as well (if necessary).

Now I am back in the previous kernel (it is a blessing they are not immediately removed), and will remain using it until I troubleshoot this problem.

What can I do to fix this? Is it a common problem?

Thanks.
Joe.

---

### Post by pestilence on 2007-06-11
If you are using the drivers of ATI (downloaded from the ATI site) then you need to rebuild them against the new ly installed Kernel.
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by Atomic Dog on 2007-06-11
This is why I dislike kernel updates being auto installed with Update Manager.  It just has the chance to break too many apps that are built against the previous version.  If your system is running fine you may want to turn off the kernel updates (or turn them off after you get your system back running smoothly with the latest kernel).

Open synaptic package manager and select the kernel & headers installed & you are using.  Click on "Package" then select "Lock Version."  New Kernel updates will not be installed once done.

---

### Post by joe.turion64x2 on 2007-06-11
In fact I am using the ATI drivers provided by the restricted drivers manager. I would have thought that they planned the update well so the video didn't break. Anyway I have disabled the update manager because my Ubuntu system (with the 'older' kernel) is just PERFECT. The next time I log in to Ubuntu I'll lock the kernel version.

Thanks.
Joe.

---

