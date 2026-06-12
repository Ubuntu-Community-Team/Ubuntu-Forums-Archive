---
title: "Firewire problem -- remounting an HD"
date: 2008-09-30
forum: Hardware
---

### Post by supercheetah on 2008-09-30
I have an issue that I hope someone can help me solve.  Essentially, I have an external HD (Western Digital) that seems to have a power saving feature.

The problem comes in when I use it with firewire.  If I let the HD idle for too long, it turns off automatically, but Ubuntu still thinks its mounted.  I am able to unmount it, but that seems to cause issues.

When I try to remount it, it doesn't work, unless I plug it into a USB port, which is a less than optimal solution.

It will work just fine if I reboot, but that's not desirable either.

I already tried reloading the kernel modules (sbp2, ohci1394, ieee1394), and that didn't help at all.

gscanbus, after letting this happen, doesn't even register the device.

The kernel did leave behind some interesting error messages though:

```

[ 1981.109648] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 1981.114629] Buffer I/O error on device sdb1, logical block 0
[ 1981.114638] lost page write due to I/O error on sdb1
[ 1981.290210] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 1981.290365] WARNING: at /build/buildd/linux-2.6.24/fs/buffer.c:1169 mark_buffer_dirty()
[ 1981.290369] Pid: 7163, comm: nautilus Not tainted 2.6.24-19-generic #1
[ 1981.290406]  [<c01b3b7a>] mark_buffer_dirty+0x7a/0x90
[ 1981.290441]  [<f89e37e8>] ext3_commit_super+0x48/0x80 [ext3]
[ 1981.290478]  [<f89e439a>] ext3_handle_error+0x6a/0xb0 [ext3]
[ 1981.290489]  [<c012d1bb>] printk+0x1b/0x20
[ 1981.290515]  [<f89e4495>] ext3_error+0x55/0x60 [ext3]
[ 1981.290551]  [<f89e1c02>] ext3_find_entry+0x4f2/0x650 [ext3]
[ 1981.290595]  [<c01a3fe5>] dput+0x85/0x100
[ 1981.290646]  [<c01c77a8>] proc_alloc_inode+0x38/0x60
[ 1981.290695]  [<c01b5ece>] invalidate_inode_buffers+0xe/0xc0
[ 1981.290717]  [<c031c6de>] lock_kernel+0x1e/0x40
[ 1981.290788]  [<f89e34ec>] ext3_lookup+0x3c/0x120 [ext3]
[ 1981.290798]  [<c01a3e14>] d_alloc+0x114/0x1a0
[ 1981.290832]  [<c01993fd>] do_lookup+0x14d/0x1c0
[ 1981.290866]  [<c019b38d>] __link_path_walk+0x6fd/0xe10
[ 1981.290870]  [<c019916b>] __follow_mount+0x1b/0x70
[ 1981.290906]  [<c01a7e73>] mntput_no_expire+0x13/0x70
[ 1981.290948]  [<c019bae5>] link_path_walk+0x45/0xc0
[ 1981.290996]  [<c01a7e73>] mntput_no_expire+0x13/0x70
[ 1981.291008]  [<c01bd49e>] sys_inotify_add_watch+0x16e/0x180
[ 1981.291044]  [<c019bd37>] do_path_lookup+0x77/0x200
[ 1981.291052]  [<c019aa8a>] getname+0xaa/0xe0
[ 1981.291070]  [<c019c79b>] __user_walk_fd+0x3b/0x60
[ 1981.291091]  [<c01953af>] vfs_lstat_fd+0x1f/0x50
[ 1981.291135]  [<c01a7e73>] mntput_no_expire+0x13/0x70
[ 1981.291147]  [<c01bd49e>] sys_inotify_add_watch+0x16e/0x180
[ 1981.291178]  [<c019545f>] sys_lstat64+0xf/0x30
[ 1981.291195]  [<c01804a0>] do_munmap+0x180/0x1f0
[ 1981.291250]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 1981.291283]  [<c0310000>] unix_stream_sendmsg+0x110/0x390
[ 1981.291314]  =======================
[ 1981.296989] Buffer I/O error on device sdb1, logical block 0
[ 1981.296999] lost page write due to I/O error on sdb1
[ 1981.359712] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 1981.359871] Buffer I/O error on device sdb1, logical block 0
[ 1981.359874] lost page write due to I/O error on sdb1
[ 1981.359960] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[ 1981.360106] Buffer I/O error on device sdb1, logical block 0
[ 1981.360108] lost page write due to I/O error on sdb1

```

Does anyone have any ideas as to what might be going on?  Are there any fixes?

---

### Post by IcarusR on 2008-09-30
sdparm will, if its sata drive, (hdparm if not) tell you if any powersaving modes are enabled & can be used to turn some off.
You'll need to check the manpage... man sdparm from terminal.
Or possibly a Western Digital utility.

---

