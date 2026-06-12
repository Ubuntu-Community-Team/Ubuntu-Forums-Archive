---
title: "chmod 666"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by Afishionado on 2007-01-03
Hello,

Stupid question time, I guess.

I have an oddball USB device that I have to have write access to the /dev entry to use. Under Debian I just run chmod 666 once and I'm one, but Ubuntu is forcing me to do that on every boot.

How can I tell whatever Ubuntu uses instead of devfs to make the device writable to users?

Wiliam

---

### Post by taurus on 2007-01-03
Is it vfat, ntfs, ext2/ext3, jfs, etc. filesystem?  Also, do you mount it from /etc/fstab or do you use the automount and where do you mount it to, mount point?

---

### Post by Afishionado on 2007-01-03
The device doesn't have a filesystem, and I don't mount it (it's the usb IR "tower" from the Lego Mindstorms toy, not a storage device). I use the BrickOS package with it, and BrickOS needs write access to the device's /dev entry.

Sorry for the confusion.

William

---

### Post by jimcooncat on 2007-01-03
Don't know anything you're talking about, but can't you just add a script to your startup?

---

### Post by Afishionado on 2007-01-03
A startup script wouldn't really work because the device node doesn't appear until the device is plugged in, and the device is hotpluggable (and I tend to hotplug it often).

Anyway, it looks like what I'm looking for is buried in the udev manpage. Sorry to bug everybody.

William

---

