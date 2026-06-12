---
title: "Jaunty Update: system does not boot anymore"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by benjiamobi on 2009-08-28
Hi to all,
 
I just updated my notebook form intrepid to jaunty. The update went
smoothly but after I rebooted the system the system is stuck and went to
the BusyBox. On intrepid everything worked fine...
 
My encrypted root device (/dev/mapper/sda1_crypt) is recognised, the
system wants to get my passphrase, the root partitions is unencrypted
and then it tries to unencrypt my next partition. (On intrepid this was
/dev/mapper/sda3_crypt on /usr). But the system waits for about 2
minutes and drops to the BusyBox.
 
I get the following system messages:
 
Unlocking the disk
/dev/disk/by-uuid/d5f140f2-af8e-4c27-82e0-92e8a3e0febe (sda1_crypt)
Enter passphrase:
key slot 0 unlocked.
Commands successful.
cryptsetup: sda1_crypt setup successfully
Begin: Waiting for encrypted source device... ...
Done.
Check cryptopts=source= bootarg cat /proc/cmdline
or missing modules, devices cat /proc/modules ls /dev
-r ALERT! /dev/disk/by-uuid/2adba953-fe57-4800-ad75-4cdd97041f0e does
not exists. Dropping to a shell!
 
BusyBox v1.10.2 ...
 
please what can i do????? i need help

---

