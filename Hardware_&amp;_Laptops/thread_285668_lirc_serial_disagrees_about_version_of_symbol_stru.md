---
title: "lirc_serial: disagrees about version of symbol struct_module"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by ColonelOops on 2006-10-27
Hi,

yesterday I updated my dapper to edgy.
Now I wanted to recompile the lirc_serial kernel module, but it doesn't work anymore. I used the howto in this forum ([http://ubuntuforums.org/showthread.php?t=163496&highlight=lirc+howto)](http://ubuntuforums.org/showthread.php?t=163496&highlight=lirc+howto)), but when i "modprobe lirc_serial" I get:
WARNING: Error inserting lirc_dev (/lib/modules/2.6.17-10-386/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_serial (/lib/modules/2.6.17-10-386/misc/lirc_serial.ko): Invalid module format

dmesg says:
[17217266.336000] lirc_dev: disagrees about version of symbol struct_module
[17217266.336000] lirc_serial: disagrees about version of symbol struct_module

Can anyone help me on this?

Cheers,
C.

---

