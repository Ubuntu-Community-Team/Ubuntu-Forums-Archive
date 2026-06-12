---
title: "Having trouble successfully installing Nvidia drivers on Hardy 8.04"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Allmont on 2009-09-28
So i'm relatively new to linux and ubuntu, and i've been trying to install drivers for my Nvidia GeForce 9800 GT. I've followed several tutorials to the best of my ability to no avail. When i attempt to install the drivers, the procedure goes well until i restart/ return to a graphical interface, the graphics card and monitor cannot be detected, and when i attempt to select what they are from the options, it ignores what i select and continues is super lo-res. I've continued to look and the drivers were not being used, and all of my attempts to fix this end up with me reverting to the default generic driver until i can figure it out. The option to use the driver does not appear in system > administration > hardware drivers at all.

If it helps at all :
Release : 8.04 (hardy)
Kernel Linux 2.6.24-24-generic
GNOME 2.22.3

And what i got from dmesg | grep -i nv

```
keith@keith-desktop:~$ dmesg | grep -i nv
[    0.000000]  BIOS-e820: 00000000dfe8ac00 - 00000000dfe8cc00 (ACPI NVS)
[   33.756899] nvidia: module license 'NVIDIA' taints kernel.
[   33.760106] NVRM: loading NVIDIA Linux x86 Kernel Module  71.86.04  Mon Jan 21 11:22:18 PST 2008
[   41.974638] NVRM: API mismatch: the client has the version 185.18.36, but
[   41.974640] NVRM: this kernel module has the version 71.86.04.  Please
[   41.974641] NVRM: make sure that this kernel module and all NVIDIA driver
[   41.974643] NVRM: components have the same version.
[   47.086590] NVRM: API mismatch: the client has the version 185.18.36, but
[   47.086593] NVRM: this kernel module has the version 71.86.04.  Please
[   47.086594] NVRM: make sure that this kernel module and all NVIDIA driver
[   47.086595] NVRM: components have the same version.
[   52.167824] NVRM: API mismatch: the client has the version 185.18.36, but
[   52.167826] NVRM: this kernel module has the version 71.86.04.  Please
[   52.167828] NVRM: make sure that this kernel module and all NVIDIA driver
[   52.167829] NVRM: components have the same version.


```


What i get from nvidia-xconfig:
```

keith@keith-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf' 
```

And so you see that there are NO video card drivers sitting around not activated:
[IMG]http://i234.photobucket.com/albums/ee59/allmont/Screenshot-1.png[/IMG]

I looked around but i couldn't see anything on updating the kernel module, or even if i can. It may be a newbie mistake, but i'm sort of worn out from trying for the past 3 weeks, about 2-3 hours a day... yeah, it took me that long.

---

### Post by lyall on 2009-09-29
Have you tried using the System > Administration > Hardware Drivers

it will show you which Nvidia video driver that is active and which ones you can install

you can alway test them and try them to see which one works the best for you

you can also try to install them from Synaptic Package Managers
by searching for Nvidia to see which ones are available

good luck and have fun learning
lyall

---

### Post by Allmont on 2009-09-29
> **lyall said:**
> Have you tried using the System > Administration > Hardware Drivers

it will show you which Nvidia video driver that is active and which ones you can install

you can alway test them and try them to see which one works the best for you

you can also try to install them from Synaptic Package Managers
by searching for Nvidia to see which ones are available

good luck and have fun learning
lyall

As i mentioned, NO drivers appear in System > Administration > Hardware Drivers..

---

### Post by Allmont on 2009-10-01
I'm still thinking it has something to do with the nvidia kernel... does anyone know of a way to update it, and recognize that update?

---

### Post by patate_fr on 2009-10-17
Hi, I had a problem with the 2.6.24-24 kernel (2.6.24-23 was fine) and my Nvidia legacy drivers for a GeForce on Hardy.
Reinstalling linux-restricted-modules & nvidia-kernel-common solved the problem.

---

### Post by mercury00 on 2010-02-18
Did this work for anyone else?

---

