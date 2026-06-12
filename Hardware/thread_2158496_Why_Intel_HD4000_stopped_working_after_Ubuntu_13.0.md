---
title: "Why Intel HD4000 stopped working after Ubuntu 13.04 upgrade?"
date: 2013-06-29
forum: Hardware
---

### Post by Eric Buist on 2013-06-29
Hi,

After upgrade to Ubuntu 13.04, screen often stays blank at boot. I noticed that the interface is responding; X.Org is just not displaying anything. I sometimes worked around the issue by rebooting multiple times or logging in to the console and typing sudo service lightdm restart (forcing me to enter my password twice).

Most recent kernel, 3.8.0-25, did not suffer from this bug, but 3D acceleration was poor, causing Minecraft to run choppy.

I suspect this is a compatibility problem with the Intel HD4000 chipset. Since the problem persists since several weeks, I don't expect any fix soon so I would have to downgrade my CPU to get an Intel HD3000 and try with that. But this is just too much work for me, and after the downgrade, the Intel HD3000 could do the same or even worse, and I would be stuck with an extra CPU I have no other motherboard to fit in.

So this Core i7 I built a few months ago is doomed to be a Windows-only machine, but I need some form of Linux to run Unison, in order to synchronize files with other machines. VirtualBox just does not work: the mouse wheel stops working periodically for the guest OS, and sometimes keyboard shortcuts stop working as well in VirtualBox. So I really need a fix for this Intel HD4000 bug, an alternative Linux distribution or a Windows alternative to Unison. Probably the third would be the simplest because I don't want to spend my weekends compiling kernels and other Linux distributions will stick me with GNOME3 whose hot corners are just a pain.

I think this graphic bug is the only important hurdle. Besides that, my Ubuntu setup was really fine, except some periodic software instabilities and problems with the mouse wheel scrolling way too fast.

Thanks in advance for any help.

---

### Post by dino99 on 2013-06-29
that issue is all over the ubuntuforums, use dconf to handle the desktop

---

### Post by Eric Buist on 2013-06-29
Hi,

What is dconf supposed to do? Can this help solving the blank screen? Or can this only tweak GNOME3 hot corners?

---

