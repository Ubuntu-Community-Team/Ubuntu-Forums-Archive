---
title: "where is linux-image-686-smp??"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by jetsaredim on 2007-02-17
I have a new Dell system that is supposed to have a Pentium D that is dual core.  I'm pretty sure that when I was running the linu-image-generic kernel package I was getting both cores showing up.  Then I upgraded the video card inside to not use the on-board to a new Nvidia 7300LE.  Looking around at all of the guides and howtos out there on Nvidia it says to install the model-specific kernel for your machine, which in my case is 686.  I just noticed that now I don't have the second processor showing up.  I also did some searching through the packages listed in the main edgy lists and I see an old 686-smp package.  Why isn't there a 686 package that supports smp?  If someone does know of one out there, where can I get it from?

---

### Post by jetsaredim on 2007-02-17
*bump*

---

### Post by nalmeth on 2007-02-17
The generic kernel supports smp, I don't know if you can get an smp kernel and the nvidia-kernel-headers to match.

If you're using nvidia, you're probably stuck without smp, at least as far as I know. Keep digging though, I am often wrong.

---

### Post by Mike'sHardLinux on 2007-02-17
Hi jetsaredim! Me again.

I wanted to clarify that you can make the nvidia module work with an smp kernel. I have the generic (smp) i686 kernel. I didn't do anything special to make it work. (I did have to tweak the xorg config file to make dual monitors work.) The kernel is the default that came with Edgy. I merely installed the nvidia restricted module, did the reconfigure thing, and it worked. Even a kernel update or 2 or 3 later, things are still working fine together.

It's hard for me to know what's wrong without knowing everything you did along the way. Maybe you could try uninstalling the nvidia driver you are using, and install the generic kernel, then follow a different tutorial to get nvidia working.

---

### Post by equilibrium on 2007-02-17
I was thinking the same thing. :(

I have the generic kernel installed on my core2duo, but only 1core seems to get used :confused:
I might end up compiling 2.6.19 or 2.6.20 myself I guess.

---

### Post by MetalMusicAddict on 2007-02-17
If your using Ubuntu-Edgy 6.10 you want to use a -generic kernel.

---

### Post by jetsaredim on 2007-02-18
Ok, so with Mike's advice I was able to get it working with the generic kernel.  I was under some silly impression that I needed the 686 kernel for the nvidia drivers to work (must be because all of the nvidia howtos to ubuntu say so).  In any case, if you've already switched over to the 686 kernel, just install the generic, reboot, then reinstall the nvidia driver (so that the driver is re-linked against the generic kernel).  Then restart X and it should be fine.

I'm still not sure I totally understand why the generic kernel package is the only smp kernel package, but whatever.

---

### Post by Turmoyl on 2007-02-18
According to [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=edgy&release=all) the generic image has replaced at least the following:

686*
K7*
K8*
AMD64*

---

