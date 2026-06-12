---
title: "k7 kernel upgrade, restricted modules broken--no nvidia or madwifi modules"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by automat on 2005-09-26
Hello everybody.  I've just switched from Gentoo to Ubuntu after destroying my system with an emerge world.  First off, I couldn't be happier with the installation.  Everything was dected and configured correctly in about half an hour, which is definitely a nice change from the day or days long Gentoo install. :D  But as I'm starting to tweak my system a bit, I've run into a problem.

I tried upgrading from the generic kernel to the k7 kernel and I can't seem to get the restricted modules to load.  I installed the image, sources, and restricted-modules and rebooted, and I lose my nvidia driver and madwifi.  I poked around in /lib/linux-restricted-modules/2.6.12-9-k7, and it looks like all the modules are installed there.  But for some reason I can't get them to load.  Do I need to edit some modules.conf somewhere?  I'm used to Gentoo, and I've never used Debian, so I'm not too familiar with the sysv init scripts and the whole filesystem layout.  If anyone could give me a pointer on getting the new kernel modules working, I'd really appreciate it.

---

### Post by automat on 2005-09-26
Nevermind.  I'm not exactly sure what happened, but it seems to be working now.  I left the k7 kernel installed with an entry in grub just in case I could figure out what was wrong.  Apparently it was still saved as the default boot because I wasn't paying a whole lot of attention on a reboot and booted into the 2.6.12-9-k7 kernel by accident.  To my surprise, everything was working.

One thing is bugging me however.  The nvidia drivers are installed and working as I get the nice nvidia splash on starting X (which is now turned off. :P), but framerates seem slower than normal.  Additionally, the open GL xscreensavers are _reallly_ choppy.  From what I can tell, everything is configured as it was on my Gentoo box... but performance is definitely not the same.  Has anyone else run into slow 3d performance with the nvidia drivers?  If so, do you have any hints on speeding it up a bit?  I'm sure this has probably been asked before, so I'll start searching... but if you happen to stumble across this and have any tricks up your sleeve, please let me know.

Thanks,
automat

---

### Post by FooManGnu on 2005-09-28
Did you try a depmod -a as the superuser?  I don't know if it would work in hoary, but it did the trick with breezy.  After I ran it I rebooted my system and it found everything (Nvidia, ethernet, etc.,)  YMMV!

---

