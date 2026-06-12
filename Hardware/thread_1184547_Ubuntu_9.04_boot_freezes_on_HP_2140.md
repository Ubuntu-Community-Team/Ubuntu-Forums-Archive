---
title: "Ubuntu 9.04 boot freezes on HP 2140"
date: 2009-06-11
forum: Hardware
---

### Post by NikoKotiniemi on 2009-06-11
My installation has worked nicely with occasional failure to boot lately but now it has completely frozen - each and every GRUB boot attempt (single OS installed), default or recovery mode causes the following (only a screencapture available since I can't cut and paste due to freeze).

Does anyone have any ideas how to go forward with this or am I forced to install a new OS?

[http://picasaweb.google.com/lh/photo/ek8n5G0stjBfGJeheNn2-g?feat=directlink]("http://picasaweb.google.com/lh/photo/ek8n5G0stjBfGJeheNn2-g?feat=directlink")

Any help appreciated!


Niko Kotiniemi

---

### Post by sbfisher on 2009-07-04
If it's any consolation, I get exactly the same problem and it seems to be some kind of conflict or incompatibility with the kernel.  It happened after I did an update and also happens with the 9.04 live CD.

Kernel 2.6.27-11-generic will boot, but kernels 2.6.28-13-generic and 2.6.28.11-generic will not.

Sad.  I hope that this gets fixed or someone knows a fix.

---

### Post by sbfisher on 2009-07-04
Ok, so after a little searching I ran across this post:

[http://myhpmini.com/forum/viewtopic.php?f=10&t=955]("http://myhpmini.com/forum/viewtopic.php?f=10&t=955").  It seems that for these kernels to boot you need to disable the "dual core" mode in the BIOS setup screen (press F10 as it boots).

Set it to single, press F10 to save the changes to the menu (weird bios).  Go to Save and Exit and press F10 again to confirm saving changes.  Try booting and it should work.

It seems this will be fixed in another Kernel (.30 or something).  Also, it seems that in 9.04 the lid close detection doesn't work so it won't sleep when you close your lid and a few other problems.

---

### Post by apoltix on 2009-07-21
Hah, that did it! Disable "dual core" mode and it worked!

I had tried putting Ubuntu and Linux Mint on different USB disks to install on my barely unwrapped 2140, and I got several errors.

Now I'm all good, thanks!

---

### Post by splin on 2009-08-22
Or Add string nosmp in kernel boot parameter at last.

---

