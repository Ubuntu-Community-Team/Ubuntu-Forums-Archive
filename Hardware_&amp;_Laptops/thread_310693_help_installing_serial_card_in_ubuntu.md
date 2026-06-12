---
title: "help installing serial card in ubuntu"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by bscook on 2006-12-01
hello.

i have a have a multiport serial card with working drivers for kernel 2.6x .. i managed to get it working great in ubuntu dapper, but don't know how to make it automatically work at boot up.

after boot the command "sudo /sbin/insmod /root/serial/serial.ko" works just fine -- all serial ports recognized.

the instructions for automatically booting are to append "8250.nr_uarts=16" option to the kernel line in grub.  however when booting ubuntu reports that this is an unrecognized option and it is ignored (i don't remember the exact wording).

the other instruction is to add the following to modprobe.conf:
```

options 8250 nr_uarts=16
install 8250 /sbin/modprobe --ignore-install 8250; /sbin/insmod /root/serial/serial.ko

```

unfortunately, there is no modprobe.conf.  i tried adding it but it made no difference.  i also tried saving it as "8250" in the modprobe.d directory, also to no effect.

can anybody help please?

- bc

---

