---
title: "Dell Latitude D810 Suspend/Hibernation/Boot problems"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by brim4brim on 2007-10-21
So after installing Ubuntu Gutsy, it takes forever to boot.

I finally got around the problem by disabling the splash in Grub and removing Usplash in Synaptic.

It now boots fine however suspend and hibernate now fail.

Both turn off the screen and seem to be working but hibernate does not turn off the computer and the computer cannot be brought out of suspend.

It can't come out of hibernation either as the computer isn't turned off.

Anyone know what the problem might be (I know I'll probably have to provide more info but I don't know what you'll need so I'll provide anything you need, just ask).

Thanks in advance.

---

### Post by ahaurw01 on 2008-02-19
Wanted to resurrect this post, I have pretty much the same problems with my D810. Suspend/hibernate worked back from Dapper but now all of a sudden it doesn't. I'm thinking of just going back to Feisty but I do like the new Gutsy... No solution seems to work for me. I've tried s2disk/s2ram/s2both but that doesn't seem to work. Anybody else out there??

Aaron

---

### Post by richardh on 2008-02-21
I have a Dell 810. Also had same problem.

Unfortunately, its a very fundamental difficulty. The only way to deal with this is either to go back to Feisty, or to recompile the kernel using SLAB instead of SLUB (I really have no idea what these are!!!!). SLUB is used in Gusty and SLAB is used in Feisty. Ubuntu people refuse point blank to go back to SLAB and the flaw and its consequences were discovered months ago - there is a discussion in the bugs reporting list. [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

I downloaded the newest version of the screen driver and recompiled the Gutsy kernel using SLAB. The best howto i found is at [http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

By the way, if you get a blank screen after a hibenate or suspend, try Ctr-Alt-Backspace This forces a reboot of X and I have found gets you back to a working system.

---

