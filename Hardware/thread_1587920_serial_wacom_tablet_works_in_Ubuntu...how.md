---
title: "serial wacom tablet works in Ubuntu...how?"
date: 2010-10-04
forum: Hardware
---

### Post by mathfeel on 2010-10-04
Hi, I am dual-booting Ubuntu and Gentoo in my new x201 tablet. The touch screen works in Ubuntu, but not in Gentoo when they are both using xorg-1.8.

But even without X, if I do
```
xxd /dev/ttyS0
``` in Ubuntu and interacts with the screen, it spits out a lot of output suggesting the serial tablet is communicating on this port. Gentoo just gives nothing.

I am interested in figure out what makes it work in Ubuntu.  Since this is a serial device, it doesn't seem to be related to any particular kernel module (e.g. wacom.ko). I also try copying the udev rule from xserver-xorg-input-wacom over, and that didn't help.

Anyone?

---

### Post by Ayuthia on 2010-10-04
EDIT: You can disregard this.  See the next post.
The only things that I know help make the Wacom devices work are:
- the wacom.ko kernel module
- the xf86-input-wacom source

I am not for sure if you need the kernel module or not, but the system needs to register the device somehow.  I am not as familiar with serial devices, but you might check the kernel source (/usr/src/linux/drivers/input/tablet/) and see if your device is found in there.  If it is, you will most likely need to compile the kernel source.  If your device is new enough, there is a chance you might need to grab the kernel source from the linuxwacom driver.

---

### Post by Favux on 2010-10-04
Hi mathfeel,

With a serial tablet pc you do not need the wacom.ko (usb kernel driver).  You just need the X driver wacom_drv.so from xf86-input-wacom (the xserver-xorg-input-wacom package in Ubuntu Lucid).
> I also try copying the udev rule from xserver-xorg-input-wacom over, and that didn't help.
Careful!  The 69-xserver-xorg-input-wacom.rules in /lib/udev/rules.d/ is different from the wacom.rules file in the linuxwacom source code.  It has some serial tablet pc rules the Ubuntu packager put in that the linuxwacom version lacks.  And xf86-input-wacom doesn't even include the wacom.rules.  I had a long discussion with the developers (& the Xorg developer) about that.

The serial tablet pc udev rules may be the difference between Ubuntu and Gentoo.  If you've knocked them off Ubuntu just reinstall the package.

By the way, the default 0.10.5 xf86-input-wacom has some bugs that affect X61's & X200's.  Jumping cursor when rotated, etc.  So you probably want to update it to 0.10.8+.  See Section 2 at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Ayuthia on 2010-10-04
It sounds like you might have solved the issue from this [thread]("http://forums.gentoo.org/viewtopic-t-847176.html").  Is that correct?

---

