---
title: "strange harddrive errors"
date: 2006-07-15
forum: Hardware &amp; Laptops
---

### Post by equilibrium on 2006-07-15
I've just had a bit of trouble with my new install of dapper. First of all I got some disk I/O errors when booting my 686-smp kernel.
 So I re-booted into my other linux drive and did a fsck on the dapper root partition. It came up with "1.1% uncontiguos files" or something
 Then on reboot the vmlinuz for 686 kernel got corrupt and the system just reset on "uncompressing linux".
 So I booted into the 386 kernel, no problems there? (same partition). I re-installed the 686-smp kernel etc. On re-boot it all seemed to be going well, got to gdm but suddenly there were disk IO errors again.

"Buffer I/O error on device /dev/hdb3"
INIT: Cannot execure "/sbin/getty"

But now after yet another reboot I am in the 686-smp kernel and it seems to be running perfectly ok?

I'm wondering if it's a harddrive problem or even memory etc?

I just hope it doesn't do it again :-? maybe my hdd is on its way out :-k

---

