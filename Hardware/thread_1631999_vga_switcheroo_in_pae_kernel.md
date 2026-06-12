---
title: "vga_switcheroo in pae kernel?"
date: 2010-11-27
forum: Hardware
---

### Post by pmunly on 2010-11-27
Hi!  I just did a fresh install of Ubuntu 10.10 on a nice new laptop with two video cards (one nvidia and one intel; Optimus technology).  I'm having trouble enabling/testing vga_switcheroo in Maverick, using kernel 2.6.35-23-generic-pae.  According to /boot/config-2.6.35-23-generic-pae it is enabled: VGA_SWITCHEROO=y, *but* there is no /sys/kernel/debug/vga_switcheroo directory, so I can't test out any of the vga_switcheroo tools.  Anybody have any ideas?  I'm contemplating compiling a custom kernel to enable VGA_SWITCHEROO as a module, but I'd rather not do that just yet.  Are there any boot-time parameters I can pass that will cause the /sys/kernel/debug/vga_switcheroo directory & files to be created?

Thanks! :)

Relevant system specs:
CPU: Intel i7 640M @ 2.8 Ghz
GPU 1: Nvidia GT 425M
GPU 2: Integrated Intel 915
RAM: 8 GB
HDD: 750 GB

---

### Post by dino99 on 2010-11-27
you might use one of the latest kernel (2.6.37)
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

some info:
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by pmunly on 2010-11-28
I tried installing the newest (2.6.37) kernel and am having basically the same results -- no vga_switcheroo directory.  I've looked at both the mentioned web pages and haven't found any indication as to why the directory wouldn't be created at startup.  I'm about out of ideas.  Any help would be appreciated.

---

### Post by mankmonjre on 2010-12-17
Hey,
I'm also facing exactly the same problem, any solution yet?

Thanks

---

### Post by favas0 on 2011-08-23
> **pmunly said:**
> Hi!  I just did a fresh install of Ubuntu 10.10 on a nice new laptop with two video cards (one nvidia and one intel; Optimus technology).  I'm having trouble enabling/testing vga_switcheroo in Maverick, using kernel 2.6.35-23-generic-pae.  According to /boot/config-2.6.35-23-generic-pae it is enabled: VGA_SWITCHEROO=y, *but* there is no /sys/kernel/debug/vga_switcheroo directory, so I can't test out any of the vga_switcheroo tools.  Anybody have any ideas?  I'm contemplating compiling a custom kernel to enable VGA_SWITCHEROO as a module, but I'd rather not do that just yet.  Are there any boot-time parameters I can pass that will cause the /sys/kernel/debug/vga_switcheroo directory & files to be created?

Thanks! :)

Relevant system specs:
CPU: Intel i7 640M @ 2.8 Ghz
GPU 1: Nvidia GT 425M
GPU 2: Integrated Intel 915
RAM: 8 GB
HDD: 750 GB

hi have you tried```
 mount -t debugfs none /sys/kernel/debug
```

now check if /sys/kernel/debug/vgaswitcheroo/switch file exists .

cheers

---

