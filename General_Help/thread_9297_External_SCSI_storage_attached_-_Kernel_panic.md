---
title: "External SCSI storage attached - Kernel panic"
date: 2004-12-27
forum: General Help
---

### Post by ennpee on 2004-12-27
Hi,

I posted this topic in server section but did not get solution. Hope to get solution here :(

I wanted to run Ubuntu linux based file server. Recently I installed Ubuntu on Dell 1750 server and booted succesfully. The boot disk was recognised as /dev/sda

Then I installed a Dell SCSI card and attached a 1.5 TB (terra Byte) external storage through SCSI port and booted. System halted with following message

starting ubuntu
pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init!

I have seen this message from many others on the Ubuntu mailing lists but no firm answer for this problem.

Only when I detach the external storage, I can still boot the system succesfully.

To find out what is wrong, I booted the system with Ubuntu CDROM after attaching the external storage and came to partition stage. I saw that external storage (1.5 TB) is now being recognised as /dev/sda whereas the original boot disk where I had installed Ununtu linux is now being recognised as /dev/sdb.

So, the culprit is that Ubuntu recognises the external storage as /dev/sda once connected to system which is acting as boot device and failing half way.
I changed the grub configuration to make /dev/sdb as boot device, attached the external storage and succesfully booted. But I don't think this is good way of running a server by tweaking system configuration files.

Any permanant solution for this ?

---

