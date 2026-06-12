---
title: "Slow KDE graphics on fglrx"
date: 2013-09-10
forum: Hardware
---

### Post by Freek07 on 2013-09-10
It's been working without any issues a few months ago but after normal system upgrade, graphics became VERY sluggish. Chaging focus on window takes more than second and there is CPU loads while focusing. Resizing, moving windows is horrible as well.
I tried fglrx from repos and official AMD beta (and non-beta, too!), nothing helps.
Desktop effects are disabled.

There IS direct rendering:

$ glxinfo | head
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
....
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series
OpenGL version string: 4.3.12441 Compatibility Profile Context 13.20.11
OpenGL shading language version string: 4.30
....


X and kernel info:

X.Org X Server 1.13.3
Release Date: 2013-03-07
[    12.939] X Protocol Version 11, Revision 0
[    12.939] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    12.939] Current Operating System: Linux Grandis 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:43:33 UTC 2013 x86_64
[    12.939] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=91aa20d4-cac7-4145-8acf-0d3d4ae59623 ro quiet splash vt.handoff=7


Any ideas?

---

