---
title: "Automatic installations with preseed ?"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by i-o on 2009-03-10
Hi,

I'm trying to get an automated installation with preseed -file to get working. I'm testing with USB-stick. My problem is that I cannot get the installation-program to read input from preseed.cfg -file.

I have used following documentation: [https://help.ubuntu.com/8.10/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/8.10/installation-guide/i386/appendix-preseed.html)

What I have tried without success:
1. I have put 'preseed.cfg' file into / and /casper locations in USB-stick - no effect.
2. I have modified /syslinux.cfg and /syslinux/syslinux.cfg -files and added line: preseed/file=/preseed.cfg
- no success

Now there must be something that I haven't understood about how this preseed-method works but I just cannot seem to figure it out myself? Resolution to my problem would be much appreciated!

---

### Post by bazzer on 2009-03-13
hmm, is your usb stick trying to be a usb-cdrom, usb-hdd or usb-fdd? I've shared your pain when trying to use a stick in usb-cdrom mode. Sorry I can't answer with anything more productive, but I'm watching for replies...

---

### Post by i-o on 2009-05-28
This one has really became a pain in my *** (~forgive my rude language). After even more experienent I haven't solved the problem.

So far I have understood that this should do the trick;
- /preseed.cfg is in the root of USB (modified version)
- /syslinux.cfg has modified row;
preseed/file=/dev/sdb1/preseed.cfg

When booting from USB it wont work.
I have also tried to seed this as a boot-parameter to installer like this; "file=/preseed.cfg"
Dont work any better.

I have also tried to boot from CD and seed the value of preseed/file as a boot-parameter to installer. The preseed.cfg has been on USB-stick. The boot-parameter has been;
"file=/dev/sdb1/preseed.cfg"
This don't work any better. Any ideas about HOW this will work would be most appreciated?

---

### Post by i-o on 2009-07-01
Well, loading the preseed -file from URL seems to work better.
When booting from any Ubuntu installation CD and using the boot parameter like this;
url=http://path.to.web.server/preseed.cfg

This works with no problems. 
I'm no longer wondering why there ain't any good guides available about preseeding since it seems to be just too weird to get it working... huoh.

---

