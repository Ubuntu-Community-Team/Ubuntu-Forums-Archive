---
title: "dual monitors with odd PCI card"
date: 2009-02-28
forum: Hardware
---

### Post by brnetonboy on 2009-02-28
I installed an old PCI (not express) video card. I've gotten dual monitors working like this before, so I know it's possible. 

Video for the boot up process got sent to the PCI card instead of the onboard, no video on onboard, then halfway through boot, no video in either, though the computer did start up ok. I set the BIOS to boot with the other one and it works ok, but no second monitor output :(

Firstly, is my video card ATI or Nvidia? I can't tell. I installed sysinfo and it tells me this about the card:

```
Number 9 Computer Company Imagine 128-II (rev 02)
Subsystem: Number 9 Comptuer Company Device 0004
```

I've gone through and installed/uninstalled nvidia 173, 177 180, etc... and I think I've made a royal mess of everything. I've also tried installing ATI drivers with envyng (NO idea what I'm doing just trying to follow these directions: [http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/](http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/))

Another thing: if I try to start NVIDIA X Server Settings, it says 

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

I tried nvidia-xconfig and it gives me a VALIDATION ERROR: ```
Data incomplete in file /etc/X11/xorg.conf.
Device section "Configured Video Device" must have a Driver line.
``` then says it backed it up and wrote the new X configuration file. But it never works. Is my video card even NVIDIA? The company that makes it went out of business in 2005, it seems.

Ubuntu 8.10

---

