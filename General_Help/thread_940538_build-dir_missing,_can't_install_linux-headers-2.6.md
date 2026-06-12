---
title: "build-dir missing, can't install linux-headers-2.6.27-5-generic"
date: 2008-10-07
forum: General Help
---

### Post by gilli4 on 2008-10-07
Hi everyone!

To ensure that my kernel supports a certain driver package (mISDN), I had to go experimental and update it to [[COLOR="Blue"]2.6.27-5-generic[/COLOR]]("http://packages.ubuntu.com/de/intrepid/linux-image-2.6.27-5-generic") (yet in RC-phase).
That worked out well and I've got my system up running. But now, when I'm trying to compile the software packages, I get an error message that reports a missing build/ directory under /lib/modules/<kernelVersion>/ .
On the [[COLOR="Blue"]forums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=361252") I found that I'd need to install the kernel-headers to solve my problem.
That worked out particulary. I could install the [linux-headers-2.6.27-5]("http://packages.ubuntu.com/de/intrepid/linux-headers-2.6.27-5"), which would be needed by their [[COLOR="Blue"]-generic[/COLOR]]("http://packages.ubuntu.com/de/intrepid/linux-headers-2.6.27-5-generic") package. I had to do it by hand because it doesn't work via package-manager yet, even after an update. Now I can't install the linux-headers-2.6.27-5-generic package because they depend on an earlier libc6 package than the one I have. But my system doesn't let me install an older version of libc6. So my build-directory is still missing and a symlink to my /usr/src/linux-headers-'uname -r'/ only makes the compiler shout "Invalid kernel version".

I'm still new to linux so I'm a bit out of ideas at the moment. I'd be thankful for any hint.

My current system is Kubuntu Hardy with kernel 2.6.27-5-generic.


Best regards,

Gilzad

---

### Post by gilli4 on 2008-10-08
Hi again everyone.

By now I managed to solve some of my problems. I could finally install the linux-headers-2.6.27-5, which depended on a *newer* version of libc6. I just downgraded the libc6 library which I had earlier and was then able to install the newer one. Well, I had to replace a lot of other libraries (gcc, cpp, g++, findutils, libgomp, libstd) and fix some x-dependencies but now I'm having the stuff installed.

My remaining problem is that the package I want to compile doesn't seem to find a standard include library, it aborts the make process right at the beginning complaining that it can't find some definitions. I know that it would work if the right header files would be found, since compiling did work on my the earlier linux kernel. I do have libc6-dev installed and I also do have the newest build-essential package installed. I googled a lot and tried to fix this all day but had no success by now. Can someone please give me any hint what I should do to make the compiler find its include libraries?

Thanks in advance.


Gilzad

Edit: More than 40 views and no answer? Is there something wrong about my post?

---

