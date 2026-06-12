---
title: "LiveCD will not boot on Dell Latitude XT"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by gohanssjn on 2009-04-28
Here is all I get after a lengthy attempt at a boot:


> modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dsp: No such file or directory.

Loading, please wait...

busyBox v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

Same disc loads fine on my desktop, all of my laptop hardware passes diagnostics.

Any ideas?

I am trying to use the LiveCD to make a bootable USB, if that matters for alternative suggestions.

---

### Post by gohanssjn on 2009-04-28
Oh goodness, I think I know the issue, and I don't think there is ANYTHING I can do to fix it :(

Whenever I go to use the LiveCD, the USB options turn off on my tablet.  But the CD drive is connected via USB because it is not an internal device.

Any ideas?  Am I just out of luck with this version of Ubuntu?

---

### Post by gohanssjn on 2009-04-28
Just trying all the variables.

I made a USB startup flash drive on my desktop.  Went to startup Ubuntu on it.  Failed.  The light on the key turned off when it tried to load.

Second attempt.  When the light turned off, I pulled the key and re-inserted it.  Worked!  The system re-mounted the device and gave it power.

What in the WORLD is going on here...

---

### Post by fredwong on 2009-04-29
I am getting the same error on my media box which is currently running Ubuntu 7.10 with AMD 64bit dual core CPU.

Have you figured out how to fix it yet?

Thanks
Fred

---

### Post by gohanssjn on 2009-04-29
Nope, only thing that works for me is to yank and reinsert the device to get it to boot.

---

