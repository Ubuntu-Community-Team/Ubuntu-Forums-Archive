---
title: "Kernel panic at boot with 2.6.24.3"
date: 2008-07-23
forum: Hardware
---

### Post by fmouse on 2008-07-23
I recently upgraded my Ubuntu installation (8.04.1) on a Dell D600 laptop as per the live update process.  Kernel version 2.6.24.3 was installed (previously the box ran kernel 2.6.24-19) and I now get a kernel panic at boot with "not syncing: VFS: Unable to mount root fs on unknown-block(0,0)".  The root fs is spec'd with a UUID (a.k.a. /dev/sda1 when booting from the previous kernel with an initrd).  Fortunately, kernel 2.6.24-19 is still on the box and is quite usable, so I'm not completely hosed.  I note several things:
[LIST]
[*]No new initrd was installed, nor is there a line for one spec'd in grub's menu.lst for the 2.6.24.3 kernels.  The most recent initrd in /boot is initrd.img-2.6.24-19 and friends.
[*]The set of modules installed in /lib/modules/2.6.24.3 is substantially smaller than that installed for earlier 2.6.24 kernels.  There seems to be no package with Ubuntu-specific modules for this kernel version in the distribution database.
[/LIST]
If I add an initrd to /boot/grub/menu.lst for 2.6.24.3 the system will boot into the new kernel, but complains about missing modules and the boot stalls out.

This looks like a bug and quacks like a bug, but I'm not as familiar with Ubuntu as I am with my other distribution (Gentoo) and hesitate to file a bug unless I get some feedback that this isn't something really obvious that I've overlooked.  I try to run everything on the box quite stock, inasmuch as possible, so if this sort of thing happens it won't be because of something weird that I've done.

It looks as if other people have had this problem too.  I find a number of references to it in various Ubuntu and Linux forums, but no solutions that apply to my situation.

Any help will be appreciated!

---

### Post by sdennie on 2008-07-23
Where did you get the 2.6.24.3 kernel?  It's not a standard Ubuntu kernel.  Are you sharing a /boot partition on the machine with gentoo and is it picking up the gentoo kernel in the grub menu?  What is the output of:

```

dpkg -l | grep 2.6.24.3

```

That should tell you whether or not the kernel was installed via a normal Ubuntu style install.

---

### Post by fmouse on 2008-07-23
Thanks for your feedback, vor.  It got me to thinking about where this kernel came from, and what might have happened.

> **vor said:**
> Where did you get the 2.6.24.3 kernel?  It's not a standard Ubuntu kernel.  Are you sharing a /boot partition on the machine with gentoo and is it picking up the gentoo kernel in the grub menu?  

The box in question is strictly Ubuntu and no, it's not a Gentoo kernel, but this gives me something to consider here.

> **vor said:**
> What is the output of:

```

dpkg -l | grep 2.6.24.3

```


Nada.  This kernel version number doesn't seem to occur in the package database.  More significantly, dpkg -S /boot/vmlinuz-2.6.24.3 doesn't turn up anything, either.  The file date on the kernel file is June 17 - over a month ago - so I expect it may be an artifact of some work I did last month trying to get support for a Broadcomm wi-fi card to run after another kernel update which left things in an awkward state as well.

> **vor said:**
> That should tell you whether or not the kernel was installed via a normal Ubuntu style install.

What probably happened here is that I built this kernel from source at some point, manually installed it in grub's menu.lst, and then deleted it from menu.lst later on.  In the update I just completed, some process probably ran update-grub, which found this kernel and re-installed stanzas for it in menu.lst.  I'm going to remove the kernel and the menu.lst entries and consider the problem solved.

Thanks!

---

### Post by sdennie on 2008-07-23
> **fmouse said:**
> 
What probably happened here is that I built this kernel from source at some point, manually installed it in grub's menu.lst, and then deleted it from menu.lst later on.  In the update I just completed, some process probably ran update-grub, which found this kernel and re-installed stanzas for it in menu.lst.  I'm going to remove the kernel and the menu.lst entries and consider the problem solved.


That sounds plausible to me.  As a gentoo user, if you ever get the urge to custom compile a kernel again, you might be interested in the very convenient debian kernel build tools (they make proper .deb kernel packages).  This tutorial is a good a starting off point: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by fmouse on 2008-07-23
> **vor said:**
> That sounds plausible to me.  As a gentoo user, if you ever get the urge to custom compile a kernel again, you might be interested in the very convenient debian kernel build tools (they make proper .deb kernel packages).  This tutorial is a good a starting off point: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Thanks, vor.  Most of the kernels I run on my other systems are custom compiled, and being kind of old-fashioned in such things, I generally prefer the "make menuconfig;make bzImage;make ...." route, but I'll certainly check out the Debian tool you reference for use on this little laptop.  I ran Debian on servers for many years and have a lot of respect for the craftsmanship that goes into it, and into the tool set that goes with it.

---

