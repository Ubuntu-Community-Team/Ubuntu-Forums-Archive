---
title: "Cannot boot, pae feature not present"
date: 2008-11-24
forum: Hardware
---

### Post by dwa12457 on 2008-11-24
I just installed Ubuntu server 8.10 on a Thinkpad T41p laptop.

The install went fine but when the computer booted for the first time, I got the message:
This kernal requires the following feature not present on the CPU:
pae
Unable to load - please use a kernal suitable to your CPU

Does 8.1 not work on this hardware?

---

### Post by dwa12457 on 2008-11-25
I found the following information somewhere else and was able to boot.

"I was able to install a working kernel by booting from the server install CD, launching a recovery shell, and running
apt-get install linux-generic"

The next time you boot, GRUB will show a "generic" entry which will then boot.

It is surprising at the Ubuntu 8.10 level that the server install process doesn't check that the system won't be bootable after installation.

---

### Post by bilbo0a on 2009-02-22
Hello,

could anyone help a newbie on how you can launch the recovery shell from the installation cd.
i have downloaded 8.10 server ubuntu, burned the cd and now i dont know how to get to the recovery shell. there is only a recovery mode which looks like it starts the whole installation process again.

Any tips and hints appreciated to i can try the same the threat started did. (trying to get this work on a old acer notebook with pentium M processer which seems to have no Pae support.

This is more for fund and to learn than anything else.

Thanks

---

