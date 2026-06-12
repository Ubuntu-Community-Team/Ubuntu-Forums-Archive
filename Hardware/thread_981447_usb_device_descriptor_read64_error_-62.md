---
title: "usb device descriptor read/64 error -62"
date: 2008-11-13
forum: Hardware
---

### Post by mattlach on 2008-11-13
Hey all,

I recently bought a DVI+USB KVM switch.  After receiving it the day before yesterday it worked like a charm, switching between my windows laptop (work) and my Ubuntu 8.10 box.

The odd thing is that next day its suddenly not working.  There was a software update through the update manager right after I installed, that may be to blame, but I don't remember what it updated.

Now when I boot up the USB component (that carries the mouse and keyboard signal) gives me an error when Xorg launches:

usb device descriptor read/64 error -62

I have searched for this error, and found some articles with a similar error (different -71 instead of -62) that suggested the ehci_hcd module is to blame (bug in the kernel) but I tried the workaround (rmmod ehci_hcd) and this didn't fix anything.

Its just really weird that it would work one day, and not the next.

Any suggestions appreciated.

---

### Post by rarsa on 2009-11-16
Did you find a solution?

I've been looking for one for about two years.

None of the solutions I've found work

The most promising was this one 

[http://ubuntuforums.org/showthread.php?t=797789](http://ubuntuforums.org/showthread.php?t=797789)

I had to add usbcore.autosuspend=-1 in the grub menu for the kernel line I'm booting with.

Still no cigar.

---

