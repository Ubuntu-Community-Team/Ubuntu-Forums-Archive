---
title: "Make USB Startup Disk"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by WJason on 2009-11-10
I downloaded UNR and "unpacked" it.  I can start up the usb-creator utility.  Point it to the UNR iso file.  It finds the USB drive itself.  But the [Make startup disk] button remains gray.  How do I get this utility to work?  Is it waiting for me to answer another question?  ~Jason

---

### Post by darkod on 2009-11-10
I replied to a same question but can not locate the thread now.

Go through them until 22-23hr back in time you'll find it. Not to write it again.

Come back if you don't find it. I could never make that button work in windows, there is a different method suggested.

---

### Post by darkod on 2009-11-10
It seems the thread is deleted, can't find.

Here is a solution:
1. On google search for and download program called unetbootin. It's free.
2. Run it and there you can select ISO option and the image of ubuntu.
3. In the bottom part select your USB stick drive.
4. Click on OK and it's done. When asked do not reboot, just close the program.

If you want the main ubuntu menu to show up (recommended) do this:
1. Open the USB stick.
2. In the root rename syslinux.cfg to syslinux.old
3. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
4. Go back and rename the whole folder isolinux to syslinux

Your stick will now be bootable and will open the main ubuntu menu, first option Try Ubuntu, second Install Ubuntu, etc.

---

### Post by WJason on 2009-11-10
Thanks!  I'll take a look.  Meanwhile, I used UNetBootin and it worked like a charm.

---

### Post by WJason on 2009-11-10
Now, how do I mark this thread "solved"?

---

