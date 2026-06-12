---
title: "Customizing LiveCD from xserver?"
date: 2008-07-12
forum: General Help
---

### Post by The_N3rd on 2008-07-12
I've spent a couple hours tinkering, trying to get this to work, but to no avail. I've successfully recreated the CD file hierarchy and extracted the squashfs image files, and then Chroot-ed into my new root filesystem.  So, now I have a fs that I want to update/tweek into a new live image.  But I don't want to apt-get everything from a terminal.  I can run startx, and get into a fresh gnome desktop.  Keep in mind, I have been doing all of this in a separate session.  But I have no mouse, and even If I reconfigure xorg.conf, I cannot gain control of it.  Is there something I'm doing wrong?  Would it be easier (or even work) to simply create a new ubuntu install on a separate computer [or partition], tweak it, then just turn that into my new squashfs image?  None of the other tutorials have gave any examples of customizing a live image, graphically.
Thank you,
The N3rd

---

### Post by VMC on 2008-07-12
> **The_N3rd said:**
> I've spent a couple hours tinkering, trying to get this to work, but to no avail. I've successfully recreated the CD file hierarchy and extracted the squashfs image files, and then Chroot-ed into my new root filesystem.  So, now I have a fs that I want to update/tweek into a new live image.  But I don't want to apt-get everything from a terminal.  I can run startx, and get into a fresh gnome desktop.  Keep in mind, I have been doing all of this in a separate session.  But I have no mouse, and even If I reconfigure xorg.conf, I cannot gain control of it.  Is there something I'm doing wrong?  Would it be easier (or even work) to simply create a new ubuntu install on a separate computer [or partition], tweak it, then just turn that into my new squashfs image?  None of the other tutorials have gave any examples of customizing a live image, graphically.
Thank you,
The N3rd

This is not exactly what you want, but here is a how-to that describes how to build your own rescue and installing what you want.
[http://www.linux.com/feature/137524](http://www.linux.com/feature/137524)

---

### Post by The_N3rd on 2008-07-12
That's the same thing I've been doing, but when it comes time to add new packages via apt, I want to be able to do everything from a fully functional desktop environment, but I seem to be having trouble getting xserver to start right.

---

