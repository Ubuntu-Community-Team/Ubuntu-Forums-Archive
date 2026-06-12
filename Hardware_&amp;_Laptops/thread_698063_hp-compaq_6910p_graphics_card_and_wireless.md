---
title: "hp-compaq 6910p graphics card and wireless"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by brunoscunha on 2008-02-15
I've received a new laptop from work and after instapling gutsy the graphics card and wireless does not work properly.
The laptop is an hp-compaq 6910p
The graphics card is a mobile GM965/GL960 integrated graphics controller and it does not run compiz.
The driver used by gutsy is a Intel experimental mod setting driver for intel integrated graphics chipsets

bruno@bruno-laptop:~$ glxinfo | grep direct
direct rendering: Yes
bruno@bruno-laptop:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
bruno@bruno-laptop:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(WW) intel(0): Bad V_BIOS checksum
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32


The integrated wireless is a Broadcom 43xx chipset family in the restrited drivers. Can't scan wireless network, I only can connect with lan cable.

Can someone help me solving this?

Thanks in advance

---

### Post by brunoscunha on 2008-02-17
Anyone please?

---

