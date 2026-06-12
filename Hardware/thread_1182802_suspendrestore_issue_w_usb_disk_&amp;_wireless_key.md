---
title: "suspend/restore issue w/ usb disk &amp; wireless keyboard on 9.04"
date: 2009-06-09
forum: Hardware
---

### Post by fructivore on 2009-06-09
Hi everyone!

I'm a former (Redhat) Linux user recently returned to the fold to check out this Ubuntu thing, and so far it's great.

There's just been one problem:  I can't seem to get Ubuntu to successfully restore after suspending (or hibernating for that matter).

Here's the setup:

 - vanilla Ubuntu 9.04 "J" 64-bit desktop
 - x2 Opteron 270
 - installed onto external USB drive (long story) mounted as /dev/sdb1
 - swap is on /dev/sdb5
 - Logitech ex110 cordless keyboard/mouse combo also on USB
 - Windows XP is on internal disk, mountable as /dev/sda1
 - grub is installed on /dev/sda, defaults to Ubuntu

Everything works great, more or less (I occasionally have sense delays on the USB drive but it doesn't interfere much with normal operation), as long as I run normally.

When I suspend the system suspends fine.  But when I restore, it only comes partially back up.  The mouse works, but not the keyboard, and there's no activity on the external disk -- it's like it won't remount or something.

What's worse is if I shut down hard and cold boot, the disk is accessible again -- but the keyboard issue persists.  It's like the Logitech cordless receiver has lost its mind.

The only solution I've been able to come up with is to change the grub default to boot to Windows (which requires a few tricks, since I have no keyboard to enter my sudo password!).  When XP starts up, it loads the Logitech Windows drivers for the EX110, which seems to reset the Logitech device after I redo the "secure keyboard" procedure.

Once that's done I can reboot as many times as I want and everything works great -- until the next time I suspend and restore.

Has anyone else seen suspend restore issues like this, with USB devices not working right on restore?  What's the solution?  Is there some way with Debian/Ubuntu to tell the USB devices to wake up as part of the restore script?

And is all of this just a simple newbie error and I just don't know where to look??

Thanks for any insight!

---

