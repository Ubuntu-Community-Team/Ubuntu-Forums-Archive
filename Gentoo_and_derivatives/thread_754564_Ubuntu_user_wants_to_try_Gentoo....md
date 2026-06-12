---
title: "Ubuntu user wants to try Gentoo..."
date: 2008-04-13
forum: Gentoo and derivatives
---

### Post by lunaz on 2008-04-13
...And dual boot with an already installed Winxp partition. I got the minimal cd from gentoo.org and booted it but got stuck after allowing US keyboard layout haha :P

Saw this error:
```

The root block device is unspecified or not detected.
Please specify a device to boot, or "shell" for a shell...

```

Don't understand what that means or how to fix it, there's no mention of that in the handbook. Google not my friend either other than to say try installing from within another distro. IS that a better way to go?

This is for an Acer Aspire 3680, wired net connection.

---

### Post by regomodo on 2008-04-15
Yes,you don't need to use a cd. you can do it from ubuntu. The live/install cd just gives you a linux environment to build your gentoo setup

Follow the gentoo handbook but just do it within ubuntu. Additionally, use the [funtoo stage3 tarball]("http://www.funtoo.org/linux/").

It'll save you a lot of time

---

### Post by mohtasham1983 on 2008-06-28
Yes, gentoo installed is pretty buggy.

Try to install it using the text version. While installing don't play around with anything. I mean don't try to work with gnome panel, or any other thing. Also, don't try to switch between options with keyboard. First make sure what option you want, and then switch to it. 

I failed to install gentoo a few times, but finally I got it installed.

---

### Post by DrPppr242 on 2008-07-05
I got a similar error once too, turned out that sata support wasn't properly configured in my kernel, so grub considered my hard drive hda but gentoo saw it as sda, was there anything related to loading the drive prior to that error message?

---

