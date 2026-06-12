---
title: "How to kill X server without rendering computer insert"
date: 2012-08-31
forum: Hardware
---

### Post by grove001 on 2012-08-31
I have a Ubuntu 12.04 box with a new Nvidia GeForce GTX 680 video card.  I can't install the linux video driver for that card, because the installer stops when it detects an X server active, & refuses to proceed.  If I use "dmlight stop" (or something near that, I forget the syntax) it kills X, but in replacement I have a monochrome blank screen.  No console, no nothing, so I can't start anything, let alone the video card driver installer.  I  also monkeyed with fstab & told it to boot to runlevel 1 (I think it was---it's supposed to be console only)  and my machine looked up so badly  I had to reinstall Ubuntu to get control of it again.

Any wisdom about killing X (or booting into non-X situation) so I can do the video card install?

Thanks for the help.

---

### Post by SlugSlug on 2012-08-31
press ctrl+alt+F1

login & then kill X ;)

---

### Post by lykwydchykyn on 2012-08-31
If you hold down shift at boot time, you should get a boot menu; one of the options should be "recovery mode".  Select this and you'll boot to a shell with no X11 running.

---

### Post by grove001 on 2012-08-31
Thanks for the tip.  That fixed things so I could get my Nvidia card device driver installed.

Regards,
Will Grove

---

### Post by Bachstelze on 2012-09-01
For further reference, the proper way to stop X without going all the way to single-user mode is

```
sudo service gdm stop
```

---

