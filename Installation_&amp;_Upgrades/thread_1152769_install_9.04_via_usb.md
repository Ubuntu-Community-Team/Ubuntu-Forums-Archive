---
title: "install 9.04 via usb"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by felicat on 2009-05-08
tried when 9.04 was still in trial last month but failed to make touchpad work normally and also my external rom was sinking into a deadlock/never-ending loop (it kept creating and closing process while the disk was inside the DVD rom) :0
who knows if this problem is gonna fixed or not?

---

### Post by pastalavista on 2009-05-08
To install to USB install unetbootin in synaptic or
```
sudo apt-get install unetbootin
``` It's a program that installs any bootable CD .iso to USB automatically and even downloads it for you if haven't already. It won't work with .img files like for the Netbook Remix. For that, you also need cdi2iso, also in synaptic.

edit: I just learned imagewriter is good to make a usb disk from an img file

---

### Post by jtsop on 2009-05-12
If you select diskimage=floppy in unetbootin it works.

---

