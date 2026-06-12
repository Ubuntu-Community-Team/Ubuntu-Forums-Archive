---
title: "motion eye on vaio fe"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by bettola on 2006-06-01
i have dapper on vaio. Everythings work but I don't know how to set and use the motion eye web cam. Any Ideas or good experiences? :KS

---

### Post by bettola on 2006-06-02
i put in /etc/modules sonypi and meye modules.
I used xawt but here the return:

sudo xawtv -c /dev/video0 -geometry 640x480 -noxv -nodga
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-686)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Nessun file o directory
v4l2: open /dev/video0: Nessun file o directory
v4l: open /dev/video0: Nessun file o directory
no video grabber device available


this is dmesg part

sonypi: Sony Programmable I/O Controller Driverv1.26.
[4294687.174000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[4294687.174000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[4294687.174000] sonypi: device allocated minor is 63
[4294687.243000] Linux video capture interface: v1.00
[4294687.250000] meye: using 2 buffers with 600k (1200k total)for capture
[4294687.286000] Adding 979956k swap on /dev/sda3.  Priority:-1 extents:1 across:979956k

help!!! :-#

---

