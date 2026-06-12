---
title: "glxinfo, glxgears segfault k-7 kernel"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by tyme on 2005-07-19
I installed Ubuntu tonight (5.04), got all the updates.  Check things out, only reporting 1gb RAM when I have 1.5gb.  Search, find out the solution is to install a kernel specific to your CPU, so I installed the K7 kernel (I have an AMD XP 2800+).  All 1.5gb of RAM are now showing up, sweet.  Of course, the default nvidia-glx packages in the repo's won't work with my new kernel - so I grab the headers for the new kernel and the installer from nvidias site (version 7667), get it installed.  Xorg.conf is set up correctly (Driver  "nvidia",  Load  "glx", etc.).  Before the change of kernels everything was working great.  Now, if I attempt to run glxgears or glxinfo they both segfault.

any ideas?  and why isn't high mem support in the default kernel??

(I'm coming from a background of using Mandake, Red Hat, Gentoo, Arch, and Ubuntu 4.10 - so you can assume I have a decent idea how to get around linux ;) )

---

### Post by kleeman on 2005-07-19
Make sure all the nvidia packages from Ubuntu are uninstalled if you are using the custom drivers. If the packages are uninstalled and the progs are still segfaulting then check to see whether /etc/init.d/nvidia-glx is still there. If so delete it and reboot.

---

### Post by tyme on 2005-07-19
Yeah, about 5 minutes after I posted, I thought...maybe I should've removed the packages I installed via synaptic.  Always comes to you after you post the question, doesn't it?

So yes, removing the packages from synaptic and reinstalling via the nvidia installer seems to have fixed my problem.  Thanks!

---

