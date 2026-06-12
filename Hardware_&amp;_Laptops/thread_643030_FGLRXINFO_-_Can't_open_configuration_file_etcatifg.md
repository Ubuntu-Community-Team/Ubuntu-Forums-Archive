---
title: "FGLRXINFO - Can't open configuration file /etc/ati/fglrxrc"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by anthonws on 2007-12-17
Hey to all!

Could anyone help me out with this?

Thanks in advance.

Ubuntu 7.10 (64Bit) + Compiz (working ok) + ATI X1250

Error:

$ LIBGL_DEBUG=verbose fglrxinfo

libGL: XF86DRIGetClientDriverName: 8.37.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.37.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:5:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
Can't open configuration file /etc/ati/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/anthon/.drirc: No such file or directory.
Can't open configuration file /etc/ati/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/anthon/.drirc: No such file or directory.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.0.6473 (8.37.6)

---

### Post by anthonws on 2007-12-27
Solved!

Bought a NVidia 6200 Card!

Cheap but really functional :)

Best wishes to ATI users.

---

