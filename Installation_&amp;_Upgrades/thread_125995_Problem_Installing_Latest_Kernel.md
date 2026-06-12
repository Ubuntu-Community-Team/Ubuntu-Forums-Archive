---
title: "Problem Installing Latest Kernel"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by ErikTheRed on 2006-02-05
I tried compiling and installing the latest kernel from kernel.org, 2.6.15.2 while using the archCK patchset. I run into errors in 2 places during the process and I am unable to build the deb for the new kernel.

The first set of errors occur when I try to patch with the 2.6.15-archCK3 patchset:
> patching file Makefile
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
patching file arch/ppc/boot/simple/Makefile
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file arch/ppc/boot/simple/Makefile.rej
patching file arch/sparc64/Kconfig
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file arch/sparc64/Kconfig.rej
patching file arch/sparc64/kernel/entry.S
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file arch/sparc64/kernel/entry.S.rej
patching file arch/sparc64/kernel/systbls.S
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file arch/sparc64/kernel/systbls.S.rej
patching file arch/sparc64/kernel/time.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file arch/sparc64/kernel/time.c.rej
patching file arch/x86_64/kernel/pci-gart.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file arch/x86_64/kernel/pci-gart.c.rej
patching file block/ll_rw_blk.c
Hunk #2 FAILED at 2612.
Hunk #3 succeeded at 2875 (offset -24 lines).
Hunk #4 succeeded at 3193 (offset -24 lines).
1 out of 4 hunks FAILED -- saving rejects to file block/ll_rw_blk.c.rej
patching file drivers/char/moxa.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file drivers/char/moxa.c.rej
patching file drivers/ide/ide-cd.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file drivers/ide/ide-cd.c.rej
patching file drivers/message/i2o/i2o_scsi.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file drivers/message/i2o/i2o_scsi.c.rej
patching file drivers/net/hamradio/mkiss.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file drivers/net/hamradio/mkiss.c.rej
patching file drivers/net/skge.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
14 out of 14 hunks ignored -- saving rejects to file drivers/net/skge.c.rej
patching file drivers/usb/input/pid.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file drivers/usb/input/pid.c.rej
patching file drivers/video/aty/atyfb_base.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file drivers/video/aty/atyfb_base.c.rej
patching file drivers/video/console/vgacon.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file drivers/video/console/vgacon.c.rej
patching file fs/reiserfs/super.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file fs/reiserfs/super.c.rej
patching file fs/ufs/super.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file fs/ufs/super.c.rej
patching file fs/ufs/util.h
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file fs/ufs/util.h.rej
patching file include/linux/blkdev.h
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file include/linux/blkdev.h.rej
patching file include/linux/skbuff.h
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file include/linux/skbuff.h.rej
patching file ipc/mqueue.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
5 out of 5 hunks ignored -- saving rejects to file ipc/mqueue.c.rej
patching file kernel/workqueue.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
15 out of 15 hunks ignored -- saving rejects to file kernel/workqueue.c.rej
patching file net/bridge/br_stp_if.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file net/bridge/br_stp_if.c.rej
patching file net/bridge/netfilter/ebt_ip.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file net/bridge/netfilter/ebt_ip.c.rej
patching file net/core/net-sysfs.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
4 out of 4 hunks ignored -- saving rejects to file net/core/net-sysfs.c.rej
patching file net/ipv4/netfilter/ip_nat_helper_pptp.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
6 out of 6 hunks ignored -- saving rejects to file net/ipv4/netfilter/ip_nat_helper_pptp.c.rej
patching file net/netlink/af_netlink.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file net/netlink/af_netlink.c.rej
patching file sound/usb/usbaudio.c
Reversed (or previously applied) patch detected!  Assume -R? [n]
Apply anyway? [n]
Skipping patch.
1 out of 1 hunk ignored -- saving rejects to file sound/usb/usbaudio.c.rej


The second set of errors occur when i try to build the .deb package:
> kernel/workqueue.c:311: error: conflicting types for &#8216;__create_workqueue&#8217;
include/linux/workqueue.h:55: error: previous declaration of &#8216;__create_workqueue&#8217; was here
kernel/workqueue.c: In function &#8216;init_workqueues&#8217;:
kernel/workqueue.c:551: error: too many arguments to function &#8216;__create_workqueue&#8217;
make[2]: *** [kernel/workqueue.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.2'
make: *** [stamp-build] Error 2


Just as a reference I loosely used [this guide.]("http://www.ubuntuforums.org/showthread.php?t=84174")
Obviously with using my kernel version and the patchset I used.

Any help here would be much appreciated.

---

### Post by madchicken on 2006-02-06
[QUOTE=ErikTheRed]I tried compiling and installing the latest kernel from kernel.org, 2.6.15.2 while using the archCK patchset. I run into errors in 2 places during the process and I am unable to build the deb for the new kernel.
...
[/QUOTE]

I think this happens 'cause you should apply these patches to the 2.6.15 kernel (not to the 2.6.15.2)

bye

---

### Post by tseliot on 2006-02-06
[QUOTE=madchicken]I think this happens 'cause you should apply these patches to the 2.6.15 kernel (not to the 2.6.15.2)

bye[/QUOTE]
I think you're right. The patch already includes the improvements of 2.6.15.2 therefore it has to be applied to kernel 2.6.15.

---

### Post by newuser111 on 2006-02-06
archck and ck patch should always applied to the original 2.6.14 or 2.6.15 kernels

not the 2.6.15x updated kernel releases because the ck patch include the updates released since

---

### Post by ErikTheRed on 2006-02-07
Oh ok thanks. There was never any explicit instruction that the original kernel was required, so that was definitely where i got confused. Thanks.

---

### Post by towsonu2003 on 2006-04-11
replies here helped me a lot too (was having the same problem). thanks to the helpers :)

---

