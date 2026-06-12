---
title: "ACPI - missing battery events on HP nx6110"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by ginapi on 2006-07-18
I recently dist-upgraded my Breezy to Dapper on my HP/compaq nx6110 Laptop. 

I have the following problem:

 AC plug/uplug events are very often uncatched. 
 I can plug/unplug, maybe 2 or 3 times and everything works fine. 
 But when the event is not chatched the state freezed and nothing more happens if I plug or unplug again.
 
I breezy everything was working fine.  
I know there are some problems with power maneger events in Dapper but I didn't found any solution.

It seems to me like something related the kernel rather than acpi. 
Anybody can help ?

Thnakyou

ginapi

---

### Post by fx5 on 2006-07-21
Yes, it's an annoying kernel-bug.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/47561](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/47561)

I posted a fix there, too. I will build new kernel-images with this patch.

While compiling...

Do you use the 686-version of the kernel? (type "uname -r").

If you are using 686-version, please try if flash-animations run smoothly. ([http://www.swishzone.com/](http://www.swishzone.com/)). If not, try if they run smoothly while moving the mouse around while playing the animation.

Thanks
fx5

---

### Post by fx5 on 2006-07-21
I made a kernel image with this patch, that fixes the problem for me:

[http://www.fx5-1.de/~fx5/Linux-HP-Notebook/linux-image-2.6.15-26-386_2.6.15-26.45fx5_i386.deb](http://www.fx5-1.de/~fx5/Linux-HP-Notebook/linux-image-2.6.15-26-386_2.6.15-26.45fx5_i386.deb)

If you try it, please let me know if it works for you. And please try the flash-issue above first, if you are using a 686-kernel normally.

---

