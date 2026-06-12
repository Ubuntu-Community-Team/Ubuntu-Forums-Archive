---
title: "DVD-RW/CD-RW Drive Not Working"
date: 2011-07-20
forum: Hardware
---

### Post by tacantara on 2011-07-20
I have a Dell XPS M1330 with a DVD/CD combo drive. I can't seem to get the system to recognize that I have media in the drive, basically the drive doesn't mount. When I try to mount through the terminal, I get the error message that the device isn't listed in fstab or mtab. Here's where it gets interesting....I can put a disk in the drive, and eject it through the button on the laptop, and through the terminal (using sudo eject /dev/sr0). So, the drive doesn't mount, yet I can eject media that wasn't recognized in the first place.

I discovered that the drive wasn't working when I went to install Windows 7 on my VirtualBox. The drive doesn't mount in Ubuntu, so the VB won't see it either.

I've loaded, and re-loaded, the libdvd files that should be in place for normal operation. Is it possible that my drive is failing? I suppose I could get an external drive and connect through USB, but I'm hoping that the problem is fixable.  Any suggestions?

---

### Post by dandnsmith on 2011-07-21
You need to narrow down the area of the fault - you've made a good start, showing that Ubuntu knows about the drive (since you can do the eject).
My next step would be to try booting from a suitable CD - that should show whether there is really a problem with the drive, or just with the Ubuntu setup.
When you insert a CD/DVD, the thing goes through 3 stages:
1) the drive recognises the insertion
2) it tries to run it up to speed
3) it tries to read track 0 to determine what is the content
Only then can the OS mount it and read the entire CD/DVD.

If you can't boot from it, then it's usually worth running a lens cleaner disc through it before deciding it's failed.

It's certainly likely that you could connect a drive through USB - I do so, when I want CD/DVD on my netbook or an aging laptop.

---

### Post by tacantara on 2011-07-21
Thanks for the advice, Derek. I will try running a cleaning disc through, and hope that it does the trick. I wish that I thought of that sooner. I've. never done a cleaning on the drive in the 4 years that I've owned the laptop, and we've traveled to some dusty places together (Iraq and Kuwait among them).

---

