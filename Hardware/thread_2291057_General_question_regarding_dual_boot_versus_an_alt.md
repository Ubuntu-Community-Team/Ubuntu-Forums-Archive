---
title: "General question regarding dual boot versus an alternative"
date: 2015-08-17
forum: Hardware
---

### Post by zuren on 2015-08-17
My dad has the following laptop:

- Dell Latitude E6500
- Core 2 Duo processor
- currently running XP Pro
  - USB and eSATA ports

He is aware that XP is no longer supported so he does not connect it to the internet.  However, it does have standalone applications installed that are valuable and he doesn't have the reinstall disks.  He is wondering if I could set it up to dual boot; keep the XP install for the couple of programs he wants and have a Ubuntu install for general internet use.  Definitely possible.

Instead, I'm wondering if it is possible to remove the XP hard drive and place it into an external enclosure to boot from when needed?  The rest of the time, he would run Ubuntu on a SSD installed in the laptop.  Or is it not that simple?  I don't know if anything gets messed up if you pluck the drive out, drop it into an enclosure and connect through a USB or eSATA connection.

Any guidance would be greatly appreciated!

Thank you

---

### Post by weatherman2 on 2015-08-17
You can't run Windows for an external drive, generally.  It may be possible to hack something but I wouldn't expect it to work reliably.  (Whereas you can boot/install Ubuntu on a USB drive easily.)

My suggestion would be to clone the existing drive to a larger one (an SSD of course if you can afford it), then setup the dual boot on the SSD.  Other than data, Ubuntu doesn't require much spare for an installation - 30GB is really plenty unless you are developing code or something.

---

### Post by weatherman2 on 2015-08-17
...although you MIGHT be able to boot the XP drive from the eSata port (not USB).  But I'd still prefer the dual boot on a single drive.  Bump your external drive or something and you'll freeze windows and maybe corrupt it or something.  If you do attempt that, be sure to backup your XP drive (make an image of it, with Clonezilla) so that if it ever crashes or gets corrupted, you'll be able to restore it.

---

### Post by darkomano on 2015-08-17
I would not try to put Windows XP to external drive - it's to complicated und not reliable. 

If the software used in Windows XP is not graphics related it is possible to transfer Windows XP to a VM (virtual machine) and run under Linux/Ubuntu. 
The XP VM (the files that represent the VM) can be moved freely to any disk (internal, external). You can later transfer the XP VM to a new computer easily - what you need - the VM files + VM software  (VirtualBox, VMware) on new computer.

---

### Post by oldfred on 2015-08-18
XP does not work with AHCI unless you slip stream new drivers when you install it.
And you have to have AHCI to use an SSD, otherwise trim will not work.

When I installed a new small SSD into my Desktop in 2011, my XP would not boot. But when I turned AHCI off, it would work. I only dual booted for a short time that way and finally gave up on the last application I was using in XP. Linux app was not quite as good, but good enough.

---

