---
title: "Nvidia: TTYs broken, but X works perfectly"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by element103 on 2009-10-10
Im on Karmic beta, did an upgrade earlier.  For each kernel upgrade I do, I'm used to dropping into tty1 (ctrl alt f1) and installing the beta nvidia driver (190.32).  However, this time around, my tty1 became a mess of garbled blue/green pixels.

- Even though the ttys were borked, gdm/X was still working fine (although without compositing so probably on some other driver)
- The ttys worked in recovery mode

I have the nvidia installer script prompts memorized by now (sad, i know haha) so I logged in and ran it blindly.  Now compositing and all the other nvidia goodies work fine, but the terminals are still broken.

It doesn't make sense to me that the low-graphics terminal could possibly break and everything else works, so I don't know where to begin.  If anyone's seen this or has suggestions on how to debug it, I'd appreciate any help.

---

### Post by prshah on 2009-10-10
> **element103 said:**
> Now compositing and all the other nvidia goodies work fine, but the terminals are still broken.

It is probably because it cannot handle a particular refresh rate for the text mode. You can change this default mode by specifying it as a kernel parameter.

To find the correct kernel parameter, add the kernel option "vga=ask" to the end of the kernel boot line during the grub bootup screen. (Post back if you want more details on this.)

This will give you a list of modes usable in text mode. Choose a suitable mode and see if it solves your problem, otherwise reboot and then select another mode. You do not necessarily have to match the selected mode to your specific resolution; you can try (at your own risk!) them in line until you hit a suitable one (771 works in almost all cases).

Apparently you can also use something called "boot up manager" (?) to do this; I don't have specific knowledge about this and cannot advise more details.

---

