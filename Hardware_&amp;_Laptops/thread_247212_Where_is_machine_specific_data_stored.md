---
title: "Where is machine specific data stored?"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by dyonisius1973 on 2006-08-30
Hi

I am trying to clone one of my servers to new hardware.
Back in the Debian days, this was a matter of booting both machines with a live CD, create filesystems on the new machine, and then rsync everything to it.
Afterward, you only need to change the initrd image (if the machine has a different controller) and /etc/modules for the right hardware.

I am trying to do this with an Ubuntu machine, but there's more to it then this I'm afraid.
The machine will boot fine, but goes into single user mode (asking for ctrl-d or root passwd). If I give ctrl-d the machine appears to startup fine...
If I login with root passwd and then look around, I see nothign strange. Going to init 2 then also no problems.
It just does not boot on itself into runlevel 2 :(

So, can somebody plz point out all the places were machine specific data is stored?

So far I found out:

/initrd.img (more general the kernel and friends)
/etc/iftab
/etc/fstab
/etc/hostname
/etc/hosts
/etc/modules

---

