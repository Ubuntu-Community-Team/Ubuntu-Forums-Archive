---
title: "mkfs.ext3 hangs while writing inode tables"
date: 2009-04-29
forum: Hardware
---

### Post by phatnutz on 2009-04-29
hope this is the right forum to post this topic, I didn't see anything that might be more specifically appropriate.

I've migrated the data off my old win xp partition on my 1TB drive, and now I want to reformat the drive and write an ext3 file system to it.  gparted and fdisk will both delete and create partitions on the drive no problem, but but any time I try to write the file system with "mkfs.ext3 /dev/sdb1" it halts while writing inode tables.  It seems to do this after writing roughly the same number of inodes each time.  Sometimes the system locks, sometimes I can still work in it.  Right now I'm writing this while still looking at the output of mkfs.ext3 /dev/sdb1:

root@hub:~# mkfs.ext3 /dev/sdb1
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
39682048 inodes, 158722192 blocks
7936109 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
4844 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Writing inode tables: 1541/4844


I'm thinking it's a physical defect on the disk, but I was able to copy all the data off that drive while it was formatted as NTFS.  It's worth noting that the drive originally had two NTFS partitions of approx. 650GB and 250GB.  I thought maybe the bad sectors are right around the space where the partition boundary was, so I tried making a 650 GB partition but it still freezes at around the same inode table.  

I looked at syslog and this seems suspect, but it doesn't mean anything to me:

[516.682929]  sdb: sdb1
[848.024232] general protection fault: 0000 [#1] SMP 
[848.024241] last sysfs file: /sys/devices/pci0000:00/0000:00:0e.0/host4/target4:0:0/4:0:0:0/type
[848.024247] Dumping ftrace buffer:
[848.024251]    (ftrace buffer empty)

The rest of the relevant syslog is below, note the mkfs.ext3 stuff:

[516.682836] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[516.682868] sd 1:0:0:0: [sdb] Write Protect is off
[516.682874] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[516.682921] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[516.682929]  sdb: sdb1
[848.024232] general protection fault: 0000 [#1] SMP 
[848.024241] last sysfs file: /sys/devices/pci0000:00/0000:00:0e.0/host4/target4:0:0/4:0:0:0/type
[848.024247] Dumping ftrace buffer:
[848.024251]    (ftrace buffer empty)
[848.024254] CPU 0 
[848.024258] Modules linked in: binfmt_misc bridge stp bnep video output input_polldev lp tuner_simple tuner_types snd_intel8x0 snd_ac97_codec tuner tvaudio ac97_bus bttv snd_seq_dummy snd_bt87x ir_common snd_seq_oss snd_pcm_oss snd_mixer_oss compat_ioctl32 videodev v4l1_compat i2c_algo_bit snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq v4l2_common videobuf_dma_sg videobuf_core snd_seq_device snd_pcm btcx_risc psmouse snd_timer tveeprom ppdev snd soundcore pcspkr serio_raw k8temp shpchp uli526x i2c_ali15x3 i2c_ali1535 i2c_ali1563 joydev parport_pc parport snd_page_alloc usbhid floppy fbcon tileblit font bitblit softcursor
[848.024341] Pid: 3891, comm: mkfs.ext3 Not tainted 2.6.28-11-generic #42-Ubuntu
[848.024345] RIP: 0010:[<ffffffff8040580c>]  [<ffffffff8040580c>] generic_make_request+0x7c/0x4b0
[848.024360] RSP: 0018:ffff88006a0856a8  EFLAGS: 00010202
[848.024364] RAX: 0000000000000000 RBX: ffff880036aeaa00 RCX: ffff8800805b0000
[848.024369] RDX: ffff88007dd7d980 RSI: 0000000000000001 RDI: ffde88007cdfb800
[848.024373] RBP: ffff88006a085738 R08: 0000000000000000 R09: ffff880036aef7f0
[848.024377] R10: ffffe20000e6a180 R11: 0000000000000000 R12: 0000000000000001
[848.024381] R13: ffff880036aeaa00 R14: 0000000000000001 R15: 0000000000000200
[848.024387] FS:  00007fb2e7c5b750(0000) GS:ffffffff80aa3000(0000) knlGS:00000000f72ab750
[848.024391] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[848.024395] CR2: 00007f168efa9e38 CR3: 000000006a16d000 CR4: 00000000000006a0
[848.024399] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[848.024404] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[848.024409] Process mkfs.ext3 (pid: 3891, threadinfo ffff88006a084000, task ffff88007dd7d980)
[848.024413] Stack:
[848.024415]  ffff88006a085728 ffffffff802b31d6 ffff88006a0856e0 0000001000000037
[848.024423]  ffff880077866230 ffffffff00000000 ffff880077850af0 ffff880036aeaa00
[848.024431]  ffff88006a085740 ffff88007f9c5c00 0000000000000001 0000000000000200
[848.024440] Call Trace:
[848.024443]  [<ffffffff802b31d6>] ? mempool_alloc+0x56/0x140
[848.024452]  [<ffffffff80405cb0>] submit_bio+0x70/0xf0
[848.024459]  [<ffffffff8030c8fe>] submit_bh+0xee/0x130
[848.024467]  [<ffffffff8030f2ea>] __block_write_full_page+0x1da/0x3b0
[848.024474]  [<ffffffff80311ed0>] ? blkdev_get_block+0x0/0x70
[848.024480]  [<ffffffff80311ed0>] ? blkdev_get_block+0x0/0x70
[848.024486]  [<ffffffff8030f5af>] block_write_full_page+0xef/0x110
[848.024493]  [<ffffffff803138a3>] blkdev_writepage+0x13/0x20
[848.024499]  [<ffffffff802b7ab2>] __writepage+0x12/0x50
[848.024506]  [<ffffffff802b8c40>] write_cache_pages+0x230/0x490
[848.024513]  [<ffffffff802b7aa0>] ? __writepage+0x0/0x50
[848.024519]  [<ffffffff802b8ebf>] generic_writepages+0x1f/0x30
[848.024526]  [<ffffffff802b8ef8>] do_writepages+0x28/0x50
[848.024532]  [<ffffffff80306f45>] __sync_single_inode+0x75/0x330
[848.024539]  [<ffffffff80307253>] __writeback_single_inode+0x53/0x1b0
[848.024545]  [<ffffffff8030baa6>] ? alloc_buffer_head+0x46/0x50
[848.024552]  [<ffffffff80307804>] generic_sync_sb_inodes+0x314/0x4e0
[848.024558]  [<ffffffff80307bb2>] writeback_inodes+0x62/0x100
[848.024564]  [<ffffffff802b85ff>] balance_dirty_pages+0x1bf/0x310
[848.024572]  [<ffffffff802b879b>] balance_dirty_pages_ratelimited_nr+0x4b/0x60
[848.024579]  [<ffffffff802b035e>] generic_perform_write+0x14e/0x1c0
[848.024585]  [<ffffffff802da135>] ? shmem_xattr_security_get+0x15/0x20
[848.024593]  [<ffffffff802da135>] ? shmem_xattr_security_get+0x15/0x20
[848.024600]  [<ffffffff802b1498>] generic_file_buffered_write+0x78/0x140
[848.024607]  [<ffffffff802b2c21>] __generic_file_aio_write_nolock+0x261/0x470
[848.024614]  [<ffffffff802b2e67>] generic_file_aio_write_nolock+0x37/0xa0
[848.024621]  [<ffffffff802e7821>] do_sync_write+0xf1/0x140
[848.024629]  [<ffffffff80268930>] ? autoremove_wake_function+0x0/0x40
[848.024638]  [<ffffffff80317df8>] ? inotify_inode_queue_event+0xd8/0x100
[848.024645]  [<ffffffff803f5ee3>] ? apparmor_file_permission+0x23/0x30
[848.024653]  [<ffffffff803d07d1>] ? security_file_permission+0x11/0x20
[848.024661]  [<ffffffff802e7eeb>] vfs_write+0xcb/0x130
[848.024668]  [<ffffffff802e8040>] sys_write+0x50/0x90
[848.024674]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[848.024681] Code: 5b 41 5c 41 5d 41 5e 41 5f c9 c3 0f 1f 40 00 31 d2 48 83 7f 08 00 0f 84 c3 00 00 00 e9 35 04 00 00 66 0f 1f 44 00 00 49 8b 7d 10 <48> 8b 47 08 48 8b 40 68 48 c1 f8 09 48 85 c0 0f 84 dc 00 00 00 
[848.024742] RIP  [<ffffffff8040580c>] generic_make_request+0x7c/0x4b0
[848.024750]  RSP <ffff88006a0856a8>
[848.024966] ---[ end trace 079a6a90705d9143 ]---48.024539]  [<ffffffff80307253>] __writeback_single_inode+0x53/0x1b0
Apr 29 20:26:14 hub kernel: [  848.024545]  [<ffffffff8030baa6>] ? alloc_buffer_head+0x46/0x50
Apr 29 20:26:14 hub kernel: [  848.024552]  [<ffffffff80307804>] generic_sync_sb_inodes+0x314/0x4e0
Apr 29 20:26:14 hub kernel: [  848.024558]  [<ffffffff80307bb2>] writeback_inodes+0x62/0x100
Apr 29 20:26:14 hub kernel: [  848.024564]  [<ffffffff802b85ff>] balance_dirty_pages+0x1bf/0x310
Apr 29 20:26:14 hub kernel: [  848.024572]  [<ffffffff802b879b>] balance_dirty_pages_ratelimited_nr+0x4b/0x60
Apr 29 20:26:14 hub kernel: [  848.024579]  [<ffffffff802b035e>] generic_perform_write+0x14e/0x1c0
Apr 29 20:26:14 hub kernel: [  848.024585]  [<ffffffff802da135>] ? shmem_xattr_security_get+0x15/0x20
Apr 29 20:26:14 hub kernel: [  848.024593]  [<ffffffff802da135>] ? shmem_xattr_security_get+0x15/0x20
Apr 29 20:26:14 hub kernel: [  848.024600]  [<ffffffff802b1498>] generic_file_buffered_write+0x78/0x140
Apr 29 20:26:14 hub kernel: [  848.024607]  [<ffffffff802b2c21>] __generic_file_aio_write_nolock+0x261/0x470
Apr 29 20:26:14 hub kernel: [  848.024614]  [<ffffffff802b2e67>] generic_file_aio_write_nolock+0x37/0xa0
Apr 29 20:26:14 hub kernel: [  848.024621]  [<ffffffff802e7821>] do_sync_write+0xf1/0x140
Apr 29 20:26:14 hub kernel: [  848.024629]  [<ffffffff80268930>] ? autoremove_wake_function+0x0/0x40
Apr 29 20:26:14 hub kernel: [  848.024638]  [<ffffffff80317df8>] ? inotify_inode_queue_event+0xd8/0x100
Apr 29 20:26:14 hub kernel: [  848.024645]  [<ffffffff803f5ee3>] ? apparmor_file_permission+0x23/0x30
Apr 29 20:26:14 hub kernel: [  848.024653]  [<ffffffff803d07d1>] ? security_file_permission+0x11/0x20
Apr 29 20:26:14 hub kernel: [  848.024661]  [<ffffffff802e7eeb>] vfs_write+0xcb/0x130
Apr 29 20:26:14 hub kernel: [  848.024668]  [<ffffffff802e8040>] sys_write+0x50/0x90
Apr 29 20:26:14 hub kernel: [  848.024674]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Apr 29 20:26:14 hub kernel: [  848.024681] Code: 5b 41 5c 41 5d 41 5e 41 5f c9 c3 0f 1f 40 00 31 d2 48 83 7f 08 00 0f 84 c3 00 00 00 e9 35 04 00 00 66 0f 1f 44 00 00 49 8b 7d 10 <48> 8b 47 08 48 8b 40 68 48 c1 f8 09 48 85 c0 0f 84 dc 00 00 00 
Apr 29 20:26:14 hub kernel: [  848.024742] RIP  [<ffffffff8040580c>] generic_make_request+0x7c/0x4b0
Apr 29 20:26:14 hub kernel: [  848.024750]  RSP <ffff88006a0856a8>
Apr 29 20:26:14 hub kernel: [  848.024966] ---[ end trace 079a6a90705d9143 ]---


So I'm not sure what to try next.  I'm probably going to try a 600 GB partition instead of a 650 GB next....

any other ideas for figuring out whats wrong, maybe I'm barking up the wrong tree?

---

### Post by lloyd_b on 2009-04-29
I'd suggest running "badblocks" on that partition, and see what shows up.  "man badblocks" in a terminal window for more info on it.

Lloyd B.

---

