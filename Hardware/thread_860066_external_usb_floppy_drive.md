---
title: "external usb floppy drive"
date: 2008-07-15
forum: Hardware
---

### Post by Bert Mariën on 2008-07-15
If got a new computer without an internal floppy drive, but I do have an external floppy drive.
When I connect it, it is seen as a "disk" and not recognized as floppy drive.
How can I get Linux to recognize an external usb floppy drive as floppy?

---

### Post by canadiandude007 on 2008-07-15
What is it you want to do with it?  Are you able to access files from a floppy disk?

Have you tried to put the floppy disk into the USB drive and then connect the USB to Linux?  And see if you can read the files?

---

### Post by Bert Mariën on 2008-07-15
I can see and read and write to the floppy; that's not the problem.
I want it to be recognized as floppy, so I use it (e.g. with startup-manager) to write a boot floppy.

So, the external floppy needs to be mounted as floppy to be recognized as such.

---

### Post by canadiandude007 on 2008-07-16
I'm not sure if you just want to use it to boot the system, but it will always be recognised as a USB drive since the only way to have it mounted as a floppy drive itself is having the floppy cable connected within the machine.

You can edit the fstab for booting purposes to automount the USB device, but I don't believe you'll be able to use an external floppy drive to be seen as equivalent to an internal floppy drive, given that it uses a USB connection.

Hope that helps!

---

