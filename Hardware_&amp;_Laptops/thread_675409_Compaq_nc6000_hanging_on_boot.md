---
title: "Compaq nc6000 hanging on boot"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by kniedzw on 2008-01-22
I just installed gutsy on my Compaq nc6000, and I'm not getting the splash screen on boot.  It just sits there, occasionally causing the hard drive LED to blink, for about two minutes before it finally fires off X.

Timestamps in dmesg show no activity during startup after kjournald is started and the kernel says that EXT3-fs has mounted the filesystem(s).  The next message is from pci_hotplug, two minutes later.

Any suggestions on how to track down this problem?  I've gone looking through the forum archives and haven't seen any posts describing similar problems, and I can't figure out specifically where the boot order is defined previous to the rc init scripts running.  (I suspect it's hanging loading one or more of the modules, but I'm really not sure how to figure that out either, since I can't seem to switch to tty7 during boot.)

Ideas?

---

### Post by kvanderslice on 2008-03-18
I just installed Gutsy Desktop on an NC6000, and am getting the same issue.  Tried disabling and blacklisting the floppy module (hung up during install with this) as recommended in other threads, but it still takes about 3 or 4 minutes to fully boot up.  Any ideas on how I can find what module is causing this hanging issue (having the EXACT same problem as the OP)

---

