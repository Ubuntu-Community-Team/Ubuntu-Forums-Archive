---
title: "Install from USB using old bios?"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by theWrkncacnter on 2009-09-27
Hi, I'd like to install ubuntu from a USB drive on an old computer, but either the bios doesn't support it, or it is too tricky to implement. 

Is there another way to install from USB? Like using a floppy disk to mount the usb drive?

Thanks

---

### Post by Mercury_Alpha on 2009-09-27
If your BIOS doesn't support booting from USB, you can try the [PLoP Boot Manager]("http://www.plop.at/en/bootmanager.html").

---

### Post by nathan726 on 2009-09-27
It took me about a month trying to solve this. I tried PLoP, but it didn't work. I tried many other floppy based boot-loaders that claimed to be able to boot a USB drive. None of them worked except for [Kexec-Loader]("http://www.solemnwarning.net/kexec-loader/").

I wrote a tutorial to explain how to do it:

[http://nathan726.webs.com/boot-usb-without-bios-support.html](http://nathan726.webs.com/boot-usb-without-bios-support.html)

---

### Post by Mighty_Joe on 2009-09-28
Can you boot from CD? [USB Boot CD]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/")

---

### Post by theWrkncacnter on 2009-11-17
I ran into trouble with the USB Boot CD, and at that point I just installed Ubuntu from CD. So problem not solved, but sidestepped.

---

### Post by efflandt on 2009-11-17
One thing about USB on an old PC that is unable to boot to it, is that it may also be USB 1.0 which would be incredibly slow.  I tried to boot from a live 9.10 USB stick that normally takes about 65 seconds to boot, and it got past the language and boot menu, but I gave up on it before it got to color splash.  The PC also only had 256 MB RAM, so that may have also been an issue.

---

