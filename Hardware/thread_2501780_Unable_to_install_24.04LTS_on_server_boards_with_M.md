---
title: "Unable to install 24.04LTS on server boards with Matrox MGA G200 graphics"
date: 2024-10-20
forum: Hardware
---

### Post by hadenough on 2024-10-20
This is basically a re-run of [this 2022 thread]("https://ubuntuforums.org/showthread.php?t=2477375"). In this case, I'm on an HP ProLiant Gen10 with:

```
01:00.1 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eH3 (rev 02)
    DeviceName: Embedded Device
    Subsystem: Hewlett Packard Enterprise iLO5 VGA
    Kernel modules: mgag200
```

However, the new and exciting difference here is that installation completes, and everything is Ok *on Wayland*. I can't use Wayland, though, since this is a headless server (with a new unmodified 24.04 desktop install), accessed over IPMI and VNC (and I can plug in a minimal VGA monitor if necessary). The reason I can't use Wayland is the VNC (from Windows). I can't find any clients that understand Wayland, so have to fall back to x11. This box previously had RHEL 8 on it and worked fine with VNC.

If I edit /etc/gdm3/custom.conf and disable Wayland then I don't get a splash screen on login (as expected, since it's still Wayland), but VNC doesn't work either. If I manually run startx then X exits with driver errors. I've tried setting [FONT=courier new]nomodeset[/FONT], and it makes no diffference.

The Xorg log initially complained that it couldn't load module mga, and:

```
MESA-LOADER: failed to open mgag200: /usr/lib/dri/mgag200_dri.so
```

Out of desperation, I eventually installed xserver-xorg-video-mga, although the links I can find are pretty clear that this is only intended for plug-in cards. The current startx output (over ssh) looks like:

```
# startx
X.Org X Server 1.21.1.11
X Protocol Version 11, Revision 0
Current Operating System: Linux merlin 6.8.0-47-generic #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 21:40:26 UTC 2024 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-6.8.0-47-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro quiet splash nomodeset vt.handoff=7
xorg-server 2:21.1.12-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.42.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 20 20:36:27 2024
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
xf86TokenToOptinfo: table is NULL
xf86TokenToOptinfo: table is NULL
error setting MTRR (base = 0x0000000084000000, size = 0x01000000, type = 1) Invalid argument (22)
error setting MTRR (base = 0x0000000084000000, size = 0x00ff0000, type = 1) Invalid argument (22)
MESA-LOADER: failed to open simpledrm: /usr/lib/dri/simpledrm_dri.so: cannot open shared object file: No such file or directory (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri, suffix _dri)
```

And the Xorg log output includes:

```
[  2126.453] (EE) MGA(0): V_BIOS address 0x0 out of range
[  2126.472] (EE) MGA(0): [drm] Direct rendering only supported with G200/G400/G450/G550.
```

There's one other thing confusing me. I have a similar Gen8 server on Ubuntu 22.04.5, also on x11, also accessed over VNC, and it all works. This has a Matrox G200EH, so should have exactly the same problem, but doesn't. The drivers in /usr/lib/x86_64-linux-gnu/dri are almost identical. I don't know how I set this up, but I disabled Wayland in some different way: /etc/gdm3/custom.conf still has the disable line commented out, but XDG_SESSION_TYPE is 'x11'.

Any ideas? I've spent all day on this and my head is hurting. I think I may have to dump 24.04 and install 22.04 instead to see if that works.

---

