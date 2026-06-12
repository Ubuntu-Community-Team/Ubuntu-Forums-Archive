---
title: "Ubuntu failing on VMware.. HELP!"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by 007isbond1 on 2009-04-18
so, basically I got ubuntu installed, everything went fine.
and now during boot I get this message and nothing else will happen:
```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t (/dev/disk/by-uuid/81ec7e43-4c83-a1a2-ba7e1e432d26) = sda(8, 5)
kinit: trying to resume from /dev/disk/by-uuid/81ec7e43-f460-4c83-a1a2-ba7e1e432d26
kinit: No resume image, doing normal boot...
_
```

how do I get past this screen into ubuntu?!

Thank you in advance.

---

### Post by lemming465 on 2009-04-19
Which version of Ubuntu, which version of vmware, is the CPU 32-bit or 64-bit, is the installed version of Ubuntu 32-bit or 64-bit, what is the host OS, and is hypervisor support on in the BIOS on the host OS?  Can you still boot a live CD-image in that VM?  If so, what does it show for "sudo fdisk -lu"?

It looks like it's getting stuck after loading the kernel but before mounting the root filesystem.  "no resume image, doing normal boot" is part of the default boot sequence, so that part is normal.

---

### Post by MyTer on 2009-10-21
I had the same problem.

Try to go to the first console with Ctrl-Alt F1

login with your username and password 
run startx

The next time You start your virtual machine, it should start in graphic mode, not text mode. 

Good luck!

---

