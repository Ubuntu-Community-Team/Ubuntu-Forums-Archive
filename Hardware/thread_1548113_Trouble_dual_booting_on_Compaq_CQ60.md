---
title: "Trouble dual booting on Compaq CQ60"
date: 2010-08-07
forum: Hardware
---

### Post by the_dark_light on 2010-08-07
I've recently tried to dual boot ubuntu with windows on my Compaq CQ60 laptop.

The laptop shipped with Vista Home Basic (rubbish! it's got NVIDIA graphics), I unfortunately need windows for a few apps so I would like to dual boot it with Ubuntu.

Since installing Ubuntu, windows refuses to load.  Partway through loading it resets and upon trying to load again it reports that "a recent hardware or software change may be preventing windows from loading"

I think I was able to get this to work a while ago, but after installing Ubuntu 10.04 I ran in to this problem.  Restoring windows from the recovery partition/recovery DVD restored it to normal working order (it should be noted that the partition structure hasn't changed since I installed linux the first time).  

I recently tried again with both Ubuntu and Mint and I've found the same problem.

Has anyone run in to a similar problem and has anyone got any ideas on how to resolve this?  It seems like the very act of replacing the boot loader with GRUB broke windows, I certainly wouldn't put it past Microsoft to pull crap like this but I'd like to think there's a perfectly innocent explanation for this.

---

### Post by the_dark_light on 2010-08-08
Also, the Linux instances seem to boot perfectly.

This one is really confusing me as I dual boot all the time, this is the first time I've run in to such a problem

---

### Post by the_dark_light on 2010-08-09
Starting to look like GRUB2 may be at fault, which would explain why I have been able to dual boot with older versions of Ubuntu.

When I get a moment I'll try to install it with GRUB1

---

