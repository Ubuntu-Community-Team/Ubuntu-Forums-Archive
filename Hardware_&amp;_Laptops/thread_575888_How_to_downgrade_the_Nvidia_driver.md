---
title: "How to downgrade the Nvidia driver?"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Hund on 2007-10-14
I'm using 7.10 RC. But I cant use the Nvidia driver (100.14.19) that the restricted driver manager gives me.

I read somewhere that it could be some problems with the newest version and if you have a dualcore processor, to solve the problem you could install the version 100.14.09.
But when I did that I'm getting this message in the log:

> NVRM: API mismatch: the client has the version 100.14.09, but this kernel module has the version 100.14.19. Please make sure that this kernel module and all NVIDIA driver components have the same version.

How do I downgrade the Nvidia driver in a proper way?

---

### Post by BobLand on 2007-10-15
> But I cant use the Nvidia driver (100.14.19) that the restricted driver manager gives me.

The driver you are using is incompatable with the kernel's version.  You **must** match the kernel version.  You don't want to downgrade, you want to upgrade.  

I'd suggest trying Synaptic.  It will usually list a few versions of the nVidia drivers.  Select the nvidia-glx-new.  When you install it, if you get errors, look at them very carefully.  The errors will tell you what version you are installing against the kernel.  

If that doesn't work, try downloading from the nvidia web site.  If that still doesn't work, try finding and compiling the source.  That way it will accommodate the various characteristics of your particular system.

Hope this helps,
bobland

---

### Post by Hund on 2007-10-15
I've forgot this thread. :) Problem solved already, I installed xserver-glx package and now I can use the version 100.14.19.

---

