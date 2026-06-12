---
title: "CPU throttling applet in Gnome"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by yukito on 2006-08-03
Hi all,

I'm new to ubuntu, and I must say that I am somewhat impressed by how well it does things out of the box. Wifi, widescreen resolution, synaptics package management. I've tried other distributions, including Debian, Gentoo, Suse, Fedora, Sourcemage, Archlinux etc, and this is really the easiest and most intuitive installation process I've ever seen. The only downside is the brown color ;)

I've had some trouble with getting cpu throttling to work though. It works just fine through the command line (echo n > /sys/devices/.../scaling_setspeed) after I've added the correct modules to /etc/modules, but the Gnome applet won't allow me to select frequencies or governors :(

It's a shame this doesn't work out of the box on systems with cpus that support it, would have made the installation flawless. I have a Celeron M processor, if that's of any use to you.

Also, is there a way to stop the powernowd daemon from being started at boot time?

Kind regards,

Wim

---

### Post by zgoda on 2006-08-04
The issue with Celeron M is present in all versions of Ubuntu since 4.10 (this was the latest where it worked out of the box).
To get frequency scaling you have to manually add scaling module name to the list of modules loaded at boot. The list resides in file /etc/modules and the module name is p4_clockmod (since Celeron M lacks more advanced features found in Pentium M processors). Open terminal window and issue command

```
$ sudo gedit /etc/modules
```

then add a line saying p4_clockmod to this file. Save, reboot, enjoy.

As the next step I would recommend changing frequency modulation daemon from powernowd to cpufreqd, as the later one is much more configurable, although it's not as easy to get working as powernowd is.

---

