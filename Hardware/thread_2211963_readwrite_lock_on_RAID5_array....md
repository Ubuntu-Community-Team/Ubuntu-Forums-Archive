---
title: "read/write lock on RAID5 array...??"
date: 2014-03-18
forum: Hardware
---

### Post by bomski on 2014-03-18
Hi everyone; I have a S/W RAID5 setup (ubuntu 12.04.3 LTS) and i'm experiencing an issue when copying files (100mb+) to the array...

Basically if I connect to the server from a client (using a samba share on the volume), I can initiate the copy... around 125-350mb in the copy hangs... if I leave the copy dialog open it will sit there for a few minutes, then continue on its way to completion...

The Ubuntu syslog displays the following:

```
Mar 18 19:07:31 media-server kernel: [ 2044.072595] INFO: task jbd2/md127-8:2673 blocked for more than 120 seconds.
Mar 18 19:07:31 media-server kernel: [ 2044.072603] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 18 19:07:31 media-server kernel: [ 2044.072607] jbd2/md127-8    D ffff88022e786e20     0  2673      2 0x00000000
Mar 18 19:07:31 media-server kernel: [ 2044.072615]  ffff880215347c58 0000000000000046 0000000000000000 ffff88023ec54580
Mar 18 19:07:31 media-server kernel: [ 2044.072623]  ffff880215347fd8 ffff880215347fd8 ffff880215347fd8 0000000000014580
Mar 18 19:07:31 media-server kernel: [ 2044.072630]  ffff880233231770 ffff88022e480000 ffff880215347c68 ffff880215347d88
Mar 18 19:07:31 media-server kernel: [ 2044.072638] Call Trace:
Mar 18 19:07:31 media-server kernel: [ 2044.072652]  [<ffffffff817479b9>] schedule+0x29/0x70
Mar 18 19:07:31 media-server kernel: [ 2044.072661]  [<ffffffff812a3c51>] jbd2_journal_commit_transaction+0x241/0x1580
Mar 18 19:07:31 media-server kernel: [ 2044.072671]  [<ffffffff810125ca>] ? __switch_to+0x12a/0x4b0
Mar 18 19:07:31 media-server kernel: [ 2044.072678]  [<ffffffff81748dde>] ? _raw_spin_lock+0xe/0x20
Mar 18 19:07:31 media-server kernel: [ 2044.072687]  [<ffffffff81089c40>] ? add_wait_queue+0x60/0x60
Mar 18 19:07:31 media-server kernel: [ 2044.072695]  [<ffffffff81072b4f>] ? try_to_del_timer_sync+0x4f/0x70
Mar 18 19:07:31 media-server kernel: [ 2044.072702]  [<ffffffff812a9398>] kjournald2+0xb8/0x240
Mar 18 19:07:31 media-server kernel: [ 2044.072709]  [<ffffffff81089c40>] ? add_wait_queue+0x60/0x60
Mar 18 19:07:31 media-server kernel: [ 2044.072716]  [<ffffffff812a92e0>] ? commit_timeout+0x10/0x10
Mar 18 19:07:31 media-server kernel: [ 2044.072729]  [<ffffffff81089170>] kthread+0xc0/0xd0
Mar 18 19:07:31 media-server kernel: [ 2044.072732]  [<ffffffff810890b0>] ? flush_kthread_worker+0xb0/0xb0
Mar 18 19:07:31 media-server kernel: [ 2044.072735]  [<ffffffff8175212c>] ret_from_fork+0x7c/0xb0
Mar 18 19:07:31 media-server kernel: [ 2044.072737]  [<ffffffff810890b0>] ? flush_kthread_worker+0xb0/0xb0
Mar 18 19:07:31 media-server kernel: [ 2044.072741] INFO: task smbd:3233 blocked for more than 120 seconds.
Mar 18 19:07:31 media-server kernel: [ 2044.072742] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 18 19:07:31 media-server kernel: [ 2044.072743] smbd            D ffff88022e786e20     0  3233   1159 0x00000000
Mar 18 19:07:31 media-server kernel: [ 2044.072745]  ffff8802162938e0 0000000000000046 ffffffff81151a77 ffff88023ec54580
Mar 18 19:07:31 media-server kernel: [ 2044.072747]  ffff880216293fd8 ffff880216293fd8 ffff880216293fd8 0000000000014580
Mar 18 19:07:31 media-server kernel: [ 2044.072750]  ffff880233231770 ffff880231fc8000 0000000000000000 ffff880231fc8000
Mar 18 19:07:31 media-server kernel: [ 2044.072752] Call Trace:
Mar 18 19:07:31 media-server kernel: [ 2044.072756]  [<ffffffff81151a77>] ? get_page_from_freelist+0x1e7/0x5c0
Mar 18 19:07:31 media-server kernel: [ 2044.072758]  [<ffffffff817479b9>] schedule+0x29/0x70
Mar 18 19:07:31 media-server kernel: [ 2044.072760]  [<ffffffff8174872d>] rwsem_down_read_failed+0xad/0x100
Mar 18 19:07:31 media-server kernel: [ 2044.072763]  [<ffffffff811524e4>] ? __alloc_pages_nodemask+0x154/0x9a0
Mar 18 19:07:31 media-server kernel: [ 2044.072766]  [<ffffffff81382944>] call_rwsem_down_read_failed+0x14/0x30
Mar 18 19:07:31 media-server kernel: [ 2044.072768]  [<ffffffff817463a4>] ? down_read+0x24/0x2b
Mar 18 19:07:31 media-server kernel: [ 2044.072771]  [<ffffffff812527fb>] ext4_da_map_blocks+0x13b/0x3a0
Mar 18 19:07:31 media-server kernel: [ 2044.072774]  [<ffffffff811e6953>] ? alloc_buffer_head+0x43/0x50
Mar 18 19:07:31 media-server kernel: [ 2044.072775]  [<ffffffff811e6ac8>] ? alloc_page_buffers+0x68/0xc0
Mar 18 19:07:31 media-server kernel: [ 2044.072778]  [<ffffffff81252a9e>] ext4_da_get_block_prep+0x3e/0xa0
Mar 18 19:07:31 media-server kernel: [ 2044.072780]  [<ffffffff811e8dee>] __block_write_begin+0x1ae/0x4e0
Mar 18 19:07:31 media-server kernel: [ 2044.072782]  [<ffffffff812a0f1f>] ? jbd2__journal_start.part.9+0x9f/0x1d0
Mar 18 19:07:31 media-server kernel: [ 2044.072785]  [<ffffffff81252a60>] ? ext4_da_map_blocks+0x3a0/0x3a0
Mar 18 19:07:31 media-server kernel: [ 2044.072787]  [<ffffffff8125680a>] ? ext4_da_write_begin+0xda/0x2e0
Mar 18 19:07:31 media-server kernel: [ 2044.072790]  [<ffffffff81256865>] ext4_da_write_begin+0x135/0x2e0
Mar 18 19:07:31 media-server kernel: [ 2044.072792]  [<ffffffff81255d97>] ? ext4_mark_inode_dirty+0x87/0x220
Mar 18 19:07:31 media-server kernel: [ 2044.072795]  [<ffffffff8114953a>] generic_perform_write+0xca/0x210
Mar 18 19:07:31 media-server kernel: [ 2044.072797]  [<ffffffff811de3a8>] ? __mark_inode_dirty+0x48/0x350
Mar 18 19:07:31 media-server kernel: [ 2044.072799]  [<ffffffff811496dd>] generic_file_buffered_write+0x5d/0x90
Mar 18 19:07:31 media-server kernel: [ 2044.072802]  [<ffffffff8114b2c6>] __generic_file_aio_write+0x1b6/0x3b0
Mar 18 19:07:31 media-server kernel: [ 2044.072804]  [<ffffffff8114b529>] generic_file_aio_write+0x69/0xd0
Mar 18 19:07:31 media-server kernel: [ 2044.072806]  [<ffffffff8124d24b>] ext4_file_write+0x8b/0xd0
Mar 18 19:07:31 media-server kernel: [ 2044.072809]  [<ffffffff811b404a>] do_sync_write+0x7a/0xb0
Mar 18 19:07:31 media-server kernel: [ 2044.072812]  [<ffffffff811b4e8e>] vfs_write+0xce/0x200
Mar 18 19:07:31 media-server kernel: [ 2044.072814]  [<ffffffff811b5512>] SyS_pwrite64+0x92/0xa0
Mar 18 19:07:31 media-server kernel: [ 2044.072817]  [<ffffffff817521dd>] system_call_fastpath+0x1a/0x1f
Mar 18 19:12:36 media-server kernel: [ 2349.192646] type=1400 audit(1395169956.102:67): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1151 comm="cupsd" pid=1151 comm="cupsd" capability=36  capname="block_suspend"
```

I've checked the array health, individual disk SMART status (short and long tests), and everything appears fine and healthy...

Has anyone experienced an issue like this? or can someone shed any light on the problem?

Many thanks...

---

