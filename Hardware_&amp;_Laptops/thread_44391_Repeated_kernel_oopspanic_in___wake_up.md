---
title: "Repeated kernel oops/panic in __wake_up"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by stevenschlansker on 2005-06-25
I am trying to boot a PowerMac G4 into Ubuntu, and I'm running into a kernel oops and/or panic which ends in a machine hang (even if it's just an oops, no panic)

The call trace is different every time, and it's never the same application causing it.  This happens during the bootup process, after mounting the root filesystem but before it starts xdm.

Here's one oops output:
> HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is r
ecommended.  mounting read-only.
Oops: kernel access of bad area, sig: 11 [#2]
PREEMPT 
NIP: 00000000 LR: C0016180 SP: EF515B20 REGS: ef515a70 TRAP: 0400    Not tainted
MSR: 40001032 EE: 0 PR: 0 FP: 0 ME: 1 IR/DR: 11
TASK = ef47c6e0[3270] 'S75sudo' THREAD: ef514000
Last syscall: 195 
GPR00: 00000000 EF515B20 EF47C6E0 EEF2DA48 00000003 00000000 EF515B88 EF515B88 
GPR08: 00000001 EEF2DA54 00000003 EF514000 00000000 100CC254 100C0000 100A0000 
GPR16: 00000000 00000000 C0610000 00000000 00000000 00000000 00000000 EEC14818 
GPR24: 00000000 00000003 00000000 EF515B88 00000001 00000000 C0686CC8 00000000 
NIP [00000000] 0x0
LR [c0016180] __wake_up_common+0x54/0x9c
Call trace:
 [c0016214] __wake_up+0x4c/0x84
 [c0034390] __wake_up_bit+0x38/0x48
 [c008976c] wake_up_inode+0x18/0x28
 [c00885d0] unlock_new_inode+0x20/0x30
 [c01f8bc0] xfs_initialize_vnode+0x238/0x334
 [c01f9fa8] vfs_init_vnode+0x44/0x5c
 [c01cac0c] xfs_iget_core+0x36c/0x67c
 [c01cb074] xfs_iget+0x158/0x1a8
 [c01e4800] xfs_dir_lookup_int+0xa8/0x10c
 [c01e9828] xfs_lookup+0x58/0x98
 [c01f66e8] linvfs_lookup+0x68/0xb0
 [c00797a8] real_lookup+0x118/0x164
 [c0079c40] do_lookup+0xb0/0xcc
 [c007a560] __link_path_walk+0x904/0x10d0
 [c007adac] link_path_walk+0x80/0x160
note: S75sudo[3270] exited with preempt_count 1

After that it hung indefinitely.  I suspect that it's my new SIIG Ultra ATA 133/100 Pro for Mac drive controller, as it worked before then.  But, I don't think it's the hardware because it works just fine under OS X.  Often the crashing program is modprobe loading the module for the card, and if I boot into emergency mode and don't touch the drives attached to that card often it will work just fine.  How can I go about fixing this?  Is it likely a driver issue or what?  Thanks,
Steven Schlansker

---

