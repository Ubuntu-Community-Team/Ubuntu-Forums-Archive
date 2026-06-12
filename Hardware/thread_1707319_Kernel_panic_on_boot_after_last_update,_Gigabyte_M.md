---
title: "Kernel panic on boot after last update, Gigabyte M1022."
date: 2011-03-15
forum: Hardware
---

### Post by dumbbuthappy on 2011-03-15
I have a Gigabyte M1022 netbook, not had automated updates in a few weeks.  So yesterday the updates are all downloaded and installed - today when turning it on I get a stack trace like this:

get_fs_type+0x33/0xb0
do_kern_mount+0x3e/0xe0
do_mount+0x1c3/0x200
sys_mount+0x6b/0xa0
syscall_call+0x7/0xb
post_kpobe_handler+0x0/0x240

and it drops me into BusyBox.  What I speculate happened at this point is that the last batch of automated updates installed a new kernel and one of the built in kernel modules is failing to initialize on this machine, and I'm supposed to use the BusyBox shell to roll back to the previous kernel somehow.  But that's just guessing, and I don't know how to use this ash shell thing to fix it.

Anyone having the same issue/know what to do?

edit: running latest Ubuntu Netbook edition

---

### Post by Artemis3 on 2011-03-17
In the meantime, restart the machine, press and hold SHIFT before it boots. It should show you grub menu options, and the older kernel should be there.

---

