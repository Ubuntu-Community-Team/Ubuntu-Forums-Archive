---
title: "USB hard-drive: can I have both 32bit and 64 bit distros?"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by jorx on 2009-08-05
Hi everybody!
I just got a big external USB hard-drive-- and was just making some plans for it.

Is it possible to have two different distros- or rather- 32 bit and 64 bit multiple boots setup? 

And is it best to use a Live USB install (usb-creator) or could I install onto the USB more like a regular internal hard-drive? (Would that sacrifice the kind of compatibility that live usb has?)

Thanks, these are important decisions for me!

---

### Post by SoftwareExplorer on 2009-08-05
> **jorx said:**
> Is it possible to have two different distros- or rather- 32 bit and 64 bit multiple boots setup?
Yes, it is, you just set up separate partitions. 

> **jorx said:**
> And is it best to use a Live USB install (usb-creator) or could I install onto the USB more like a regular internal hard-drive? (Would that sacrifice the kind of compatibility that live usb has?)
If it's not flash memory, I would install it like you would to a normal hard disk. It should be just as compatible either way.

---

### Post by SoftwareExplorer on 2009-08-05
The reason not to use the normal install with flash memory is it sets up swap on it by default. Swap is rewritten alot and flash memory has a limited amount of rewrites in it's lifetime.

On the other hand, the USB-creator boots slow and waits for you to select your language at boot-up. However, it doesn't create a swap as far as I know.

---

### Post by jorx on 2009-08-05
Sweet- it has been working flawlessly so far- until it quite booting just recently!
In the middle of boot it says 
"mount: mounting /root to /dev/root failed: No such file or directory" and sends me to the "BusyBox" which has no shutdown or reboot command- and I'm helpless!

I'm going to mark this thread as solved and make a new thread for this problem. Thanks!

---

### Post by SoftwareExplorer on 2009-08-05
That's a good idea because more people will see your problem. Your Welcome.

---

