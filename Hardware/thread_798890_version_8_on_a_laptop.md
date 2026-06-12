---
title: "version 8 on a laptop"
date: 2008-05-18
forum: Hardware
---

### Post by PadreSol on 2008-05-18
I thought that installing ubuntu would be simple, painless, easy.

I tried to have a dual-boot system but I started that install to create a new partition and leav the existing for a dual-boot.  It started and was running fine, but ubunto put the laptop to sleep mid-way through.  The windows partition was wiped out.  Not a good fail back mechanism.

Now ubuntu is installed but it can't see the dvd drive.
How can it install from the drive then after installation not see that drive?  Makes no *bleep* sense.

Laptop is a HP pavilion zv5000.  How to I configure hardware under ubuntu?

---

### Post by PadreSol on 2008-05-18
Attached an external usb dvd and it doesn't see that either.

Is this simply a kernel issue? Do I need to rebuild the kernel to handle this hardware?  It doesn't add up....  I still don't understand how it can install from the internal dvd but it now can't see it.

---

### Post by PadreSol on 2008-05-18
Can anyone recommend a good site for laptop problems? debian or ubuntu I guess

---

### Post by ASULutzy on 2008-05-18
It might help if you explain in better detail what exactly you did and what you were trying to do and then what occurred. I'm having a bit of a hard time following your post.

---

### Post by PadreSol on 2008-05-18
...rebuilding a new kernel from latest sources... I will see if that helps...

---

### Post by PadreSol on 2008-05-27
I have been able to mount audio cds, but dvds are flakey. Tried to update to the latest firmware for the drive but the firmware updater won't run under Wine. All in all the laptop seems better when running under the new kernel.  I built from 2.6.25.4 sources and made a monolithich (non-modular) kernel without initramfs. Things just seem to work better when using a kernel built specifically for a particular make/model.

---

