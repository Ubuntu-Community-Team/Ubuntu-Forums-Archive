---
title: "Sata? problem, uninterruptible processes"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by ddamoen on 2006-12-25
Motherboard: Asus A8N-Sli Premium
Two identical harddisks: Samsung 400GB SATA HD400LJ
Using Ubuntu 6.10 x86 although AMD Athlon 64 processor.
uname -a: Linux *** 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

This has happened now twice (I've had Ubuntu for a week and half now), the first time I don't remember much except dmesg showed some repeating problems but this second time I've gathered some evidence as much as a newbie linux used could.

Oh ! The first time happened when I was playing with WINE and accidentally made hard links in ~/.wine/dosdevices/<drive letter>: to point to my games folder, tried to play eduke3d and it wouldn't start, looked at the .exe with nano and it showed garbage after a while of "doing nothing", after the reboot, the file was back to normal again. Weird huh?

Second time: I opened gThumb and it went frozen, tried to close it and after a while I was greeted by "Force quit" or something else -buttoned dialog. Clicked force quit. It closed. I tried again and the same happened.

Don't remember did I open "Applications>Accessories>Disk Usage Analyzer" first or later, but it froze also.


Now I had to have a look at dmesg and there it was, those ah-so-familiar-looking error messages: > 
Dec 25 11:03:23 kajakki kernel: [17179919.196000] ata4: status=0x51 { DriveReady SeekComplete Error }
Dec 25 11:03:23 kajakki kernel: [17179919.196000] ata4: error=0x84 { DriveStatusError BadCRC }
Dec 25 11:03:23 kajakki kernel: [17179919.204000] ata4: status=0x51 { DriveReady SeekComplete Error }
Dec 25 11:03:23 kajakki kernel: [17179919.204000] ata4: error=0x84 { DriveStatusError BadCRC }
Dec 25 11:03:55 kajakki kernel: [17179951.244000] ata4: status=0xd0 { Busy }
Dec 25 11:03:55 kajakki kernel: [17179951.244000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:03:55 kajakki kernel: [17179951.244000] sdb: Current: sense key: Aborted Command
Dec 25 11:03:55 kajakki kernel: [17179951.244000]     Additional sense: Scsi parity error
Dec 25 11:03:55 kajakki kernel: [17179951.244000] end_request: I/O error, dev sdb, sector 297756967
Dec 25 11:04:25 kajakki kernel: [17179981.244000] ata4: status=0xd0 { Busy }
Dec 25 11:04:25 kajakki kernel: [17179981.244000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:04:25 kajakki kernel: [17179981.244000] sdb: Current: sense key: Aborted Command
Dec 25 11:04:25 kajakki kernel: [17179981.244000]     Additional sense: Scsi parity error
Dec 25 11:04:25 kajakki kernel: [17179981.244000] end_request: I/O error, dev sdb, sector 19343
Dec 25 11:04:55 kajakki kernel: [17180011.244000] ata4: status=0xd0 { Busy }
Dec 25 11:04:55 kajakki kernel: [17180011.244000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:04:55 kajakki kernel: [17180011.244000] sdb: Current: sense key: Aborted Command
Dec 25 11:04:55 kajakki kernel: [17180011.244000]     Additional sense: Scsi parity error
Dec 25 11:04:55 kajakki kernel: [17180011.244000] end_request: I/O error, dev sdb, sector 19351
Dec 25 11:05:25 kajakki kernel: [17180041.244000] ata4: status=0xd0 { Busy }
Dec 25 11:05:25 kajakki kernel: [17180041.244000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:05:25 kajakki kernel: [17180041.244000] sdb: Current: sense key: Aborted Command
Dec 25 11:05:25 kajakki kernel: [17180041.244000]     Additional sense: Scsi parity error
Dec 25 11:05:25 kajakki kernel: [17180041.244000] end_request: I/O error, dev sdb, sector 19359
Dec 25 11:05:55 kajakki kernel: [17180071.244000] ata4: status=0xd0 { Busy }
Dec 25 11:05:55 kajakki kernel: [17180071.244000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:05:55 kajakki kernel: [17180071.244000] sdb: Current: sense key: Aborted Command
Dec 25 11:05:55 kajakki kernel: [17180071.244000]     Additional sense: Scsi parity error
Dec 25 11:05:55 kajakki kernel: [17180071.244000] end_request: I/O error, dev sdb, sector 19367
Dec 25 11:06:25 kajakki kernel: [17180101.244000] ata4: status=0xd0 { Busy }
Dec 25 11:06:25 kajakki kernel: [17180101.244000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:06:25 kajakki kernel: [17180101.244000] sdb: Current: sense key: Aborted Command
Dec 25 11:06:25 kajakki kernel: [17180101.244000]     Additional sense: Scsi parity error
Dec 25 11:06:25 kajakki kernel: [17180101.244000] end_request: I/O error, dev sdb, sector 19375
Dec 25 11:06:55 kajakki kernel: [17180131.248000] ata4: status=0xd0 { Busy }
Dec 25 11:06:55 kajakki kernel: [17180131.248000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:06:55 kajakki kernel: [17180131.248000] sdb: Current: sense key: Aborted Command
Dec 25 11:06:55 kajakki kernel: [17180131.248000]     Additional sense: Scsi parity error
Dec 25 11:06:55 kajakki kernel: [17180131.248000] end_request: I/O error, dev sdb, sector 19383
Dec 25 11:07:25 kajakki kernel: [17180161.248000] ata4: status=0xd0 { Busy }
Dec 25 11:07:25 kajakki kernel: [17180161.248000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:07:25 kajakki kernel: [17180161.248000] sdb: Current: sense key: Aborted Command
Dec 25 11:07:25 kajakki kernel: [17180161.248000]     Additional sense: Scsi parity error
Dec 25 11:07:25 kajakki kernel: [17180161.248000] end_request: I/O error, dev sdb, sector 19391
Dec 25 11:07:55 kajakki kernel: [17180191.248000] ata4: status=0xd0 { Busy }
Dec 25 11:07:55 kajakki kernel: [17180191.248000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:07:55 kajakki kernel: [17180191.248000] sdb: Current: sense key: Aborted Command
Dec 25 11:07:55 kajakki kernel: [17180191.248000]     Additional sense: Scsi parity error
Dec 25 11:07:55 kajakki kernel: [17180191.248000] end_request: I/O error, dev sdb, sector 19399
Dec 25 11:08:25 kajakki kernel: [17180221.248000] ata4: status=0xd0 { Busy }
Dec 25 11:08:25 kajakki kernel: [17180221.248000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:08:25 kajakki kernel: [17180221.248000] sdb: Current: sense key: Aborted Command
Dec 25 11:08:25 kajakki kernel: [17180221.248000]     Additional sense: Scsi parity error
Dec 25 11:08:25 kajakki kernel: [17180221.248000] end_request: I/O error, dev sdb, sector 19407
Dec 25 11:08:55 kajakki kernel: [17180251.248000] ata4: status=0xd0 { Busy }
Dec 25 11:08:55 kajakki kernel: [17180251.248000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:08:55 kajakki kernel: [17180251.248000] sdb: Current: sense key: Aborted Command
Dec 25 11:08:55 kajakki kernel: [17180251.248000]     Additional sense: Scsi parity error
Dec 25 11:08:55 kajakki kernel: [17180251.248000] end_request: I/O error, dev sdb, sector 19415
Dec 25 11:09:25 kajakki kernel: [17180281.248000] ata4: status=0xd0 { Busy }
Dec 25 11:09:25 kajakki kernel: [17180281.248000] sd 3:0:0:0: SCSI error: return code = 0x8000002
Dec 25 11:09:25 kajakki kernel: [17180281.248000] sdb: Current: sense key: Aborted Command
Dec 25 11:09:25 kajakki kernel: [17180281.248000]     Additional sense: Scsi parity error
Dec 25 11:09:25 kajakki kernel: [17180281.248000] end_request: I/O error, dev sdb, sector 19423
Dec 25 11:09:55 kajakki kernel: [17180311.248000] ata4: status=0xd0 { Busy }


After that, I looked around the net with no explanation to these but somewhere I came across "uninterruptible processes", went to "System monitor" and it shows two gtumb, baobab and gqview as "Uninterruptible". Couldn't kill nor end process them.

Also on the same round I found that pressing ctrl+scrolllock I could dump some stuff that could help in tracing the problem, dmesg output of that command is here (cut the parts where those uninterruptible programs stood):> [17181648.396000] gqview        D E963BD84     0  4813      1          4861  4775 (NOTLB)
[17181648.396000]        e963bde8 00000086 00000000 e963bd84 c011aa69 00000000 00000001 00000001 
[17181648.396000]        774ccd00 003d09e6 00000000 e963a000 e963bda8 c011cdf8 0000000a dfc38668 
[17181648.396000]        dfc38560 df928560 c1806ce0 7789d600 003d09e6 003d0900 00000000 00121eac 
[17181648.396000] Call Trace:
[17181648.396000]  <c011aa69> __wake_up_common+0x39/0x60  <c011cdf8> __wake_up+0x38/0x50
[17181648.396000]  <c026ad18> sock_wfree+0x38/0x40  <c026ca2a> __kfree_skb+0x4a/0x110
[17181648.396000]  <c02da2b3> __mutex_lock_slowpath+0x53/0x8d  <c02da2fc> .text.lock.mutex+0xf/0x23
[17181648.396000]  <c017899b> do_lookup+0x9b/0x160  <c017a243> __link_path_walk+0x133/0xf20
[17181648.396000]  <c017b081> link_path_walk+0x51/0xf0  <c017b368> do_path_lookup+0xb8/0x260
[17181648.396000]  <c0179f07> getname+0xa7/0xd0  <c017bdeb> __user_walk_fd+0x3b/0x60
[17181648.396000]  <c01745d2> vfs_stat_fd+0x22/0x60  <c01746af> sys_stat64+0xf/0x30
[17181648.396000]  <c016b0b9> vfs_read+0x119/0x180  <c016b5d1> sys_read+0x41/0x70
[17181648.396000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17181648.396000] baobab        D EB603E14     0  4775      1          4813  4768 (NOTLB)
[17181648.396000]        eb603e28 00000082 00000002 eb603e14 00000060 0000061b 00000000 dfaada40 
[17181648.396000]        99629f00 003d09c3 00000001 eb602000 00000000 00000000 00000009 c1964b98 
[17181648.396000]        c1964a90 c03686c0 c1806ce0 999fa800 003d09c3 00000000 00000000 c014ba30 
[17181648.396000] Call Trace:
[17181648.396000]  <c014ba30> find_get_page+0x20/0x50  <c016c899> __find_get_block_slow+0x89/0x170
[17181648.396000]  <c02d9856> io_schedule+0x26/0x30  <c016d725> sync_buffer+0x35/0x40
[17181648.396000]  <c02d9f4d> __wait_on_bit_lock+0x3d/0x70  <c016d6f0> sync_buffer+0x0/0x40
[17181648.396000]  <c016d6f0> sync_buffer+0x0/0x40  <c02d9ffd> out_of_line_wait_on_bit_lock+0x7d/0x90
[17181648.396000]  <c01361d0> wake_bit_function+0x0/0x60  <c016d899> __lock_buffer+0x29/0x30
[17181648.396000]  <f8933c03> do_get_write_access+0x2b3/0x560 [jbd]  <f8934116> start_this_handle+0x226/0x410 [jbd]
[17181648.396000]  <f8933ed0> journal_get_write_access+0x20/0x40 [jbd]  <f89732eb> ext3_reserve_inode_write+0x6b/0xa0 [ext3]
[17181648.396000]  <f8973343> ext3_mark_inode_dirty+0x23/0x50 [ext3]  <f89767cb> ext3_dirty_inode+0x7b/0x90 [ext3]
[17181648.396000]  <c018e904> __mark_inode_dirty+0x34/0x190  <c017d990> filldir64+0x0/0xe0
[17181648.396000]  <c017d990> filldir64+0x0/0xe0  <c017dbd7> vfs_readdir+0xa7/0xb0
[17181648.396000]  <c017dc4f> sys_getdents64+0x6f/0xc0  <c0102fbb> sysenter_past_esp+0x54/0x79
[17181648.396000] gthumb        D EF12FC94     0  4733      1          4754  4612 (NOTLB)
[17181648.396000]        ef12fca8 00200086 00000002 ef12fc94 f39a9640 c01d3d40 c016cc57 01f273ff 
[17181648.396000]        1b5c8d00 003d09b9 f35a2824 ef12e000 f7f0ad38 0f939ff8 00000003 ee15b668 
[17181648.396000]        ee15b560 c03686c0 c1806ce0 1b5c8d00 003d09b9 00000000 00000000 00001000 
[17181648.396000] Call Trace:
[17181648.396000]  <c01d3d40> generic_make_request+0x150/0x200  <c016cc57> __find_get_block+0x87/0x1a0
[17181648.396000]  <c01d5c85> submit_bio+0x55/0x100  <c02d9856> io_schedule+0x26/0x30
[17181648.396000]  <c016d725> sync_buffer+0x35/0x40  <c02da052> __wait_on_bit+0x42/0x70
[17181648.396000]  <c016d6f0> sync_buffer+0x0/0x40  <c016d6f0> sync_buffer+0x0/0x40
[17181648.396000]  <c02da0fd> out_of_line_wait_on_bit+0x7d/0x90  <c01361d0> wake_bit_function+0x0/0x60
[17181648.396000]  <c016d664> __wait_on_buffer+0x24/0x30  <f8978c59> ext3_find_entry+0xf9/0x630 [ext3]
[17181648.396000]  <c017cd07> send_sigio_to_task+0xf7/0x120  <c02d0b50> unix_write_space+0x80/0x90
[17181648.396000]  <c026ad18> sock_wfree+0x38/0x40  <c026ca2a> __kfree_skb+0x4a/0x110
[17181648.396000]  <f897a83c> ext3_lookup+0x3c/0x100 [ext3]  <c0182ef9> d_alloc+0x119/0x1b0
[17181648.396000]  <c0178a27> do_lookup+0x127/0x160  <c017a243> __link_path_walk+0x133/0xf20
[17181648.396000]  <c017b081> link_path_walk+0x51/0xf0  <c017b368> do_path_lookup+0xb8/0x260
[17181648.396000]  <c0179f07> getname+0xa7/0xd0  <c017bdeb> __user_walk_fd+0x3b/0x60
[17181648.396000]  <c017450f> vfs_lstat_fd+0x1f/0x50  <c017458f> sys_lstat64+0xf/0x30
[17181648.396000]  <c02dc0db> do_page_fault+0x3db/0x6f0  <c02dbd00> do_page_fault+0x0/0x6f0
[17181648.396000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17181648.396000] gthumb        D EA433DD4     0  4754      1          4756  4733 (NOTLB)
[17181648.396000]        ea433de8 00000082 00000002 ea433dd4 c011aa69 00000000 00000001 00000001 
[17181648.396000]        b37afa00 003d09bd 00000000 ea432000 ea433da8 c011cdf8 00000001 c1959b98 
[17181648.396000]        c1959a90 c03686c0 c1806ce0 b37afa00 003d09bd 003d0900 00000000 00000000 
[17181648.396000] Call Trace:
[17181648.396000]  <c011aa69> __wake_up_common+0x39/0x60  <c011cdf8> __wake_up+0x38/0x50
[17181648.396000]  <c026ad18> sock_wfree+0x38/0x40  <c026ca2a> __kfree_skb+0x4a/0x110
[17181648.396000]  <c02da2b3> __mutex_lock_slowpath+0x53/0x8d  <c02da2fc> .text.lock.mutex+0xf/0x23
[17181648.396000]  <c017899b> do_lookup+0x9b/0x160  <c017a243> __link_path_walk+0x133/0xf20
[17181648.396000]  <c017b081> link_path_walk+0x51/0xf0  <c017b368> do_path_lookup+0xb8/0x260
[17181648.396000]  <c0179f07> getname+0xa7/0xd0  <c017bdeb> __user_walk_fd+0x3b/0x60
[17181648.396000]  <c017450f> vfs_lstat_fd+0x1f/0x50  <c017458f> sys_lstat64+0xf/0x30
[17181648.396000]  <c02dc0db> do_page_fault+0x3db/0x6f0  <c02dbd00> do_page_fault+0x0/0x6f0
[17181648.396000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17181648.396000] gthumb        S EB635668     0  4756      1          4758  4754 (NOTLB)
[17181648.396000]        ea431e98 00200082 00000009 eb635668 eb635560 eb635030 c1806ce0 114b5000 
[17181648.396000]        89fedc00 003d09bd 00000000 ea430000 00000000 ea430000 00000006 f5659b98 
[17181648.396000]        f5659a90 c1959a90 c1806ce0 89fedc00 003d09bd 00000000 00000000 eb635560 
[17181648.396000] Call Trace:
[17181648.396000]  <c0125988> do_exit+0x498/0x840  <c02d9e85> schedule_timeout+0x75/0xc0
[17181648.396000]  <c0139645> get_futex_key+0x45/0x110  <c0125d67> do_group_exit+0x37/0x80
[17181648.396000]  <c013643d> add_wait_queue+0x1d/0x50  <c013a479> do_futex+0x799/0x9d0
[17181648.396000]  <c010266b> do_notify_resume+0x8b/0x6c0  <c011bde0> default_wake_function+0x0/0x10
[17181648.396000]  <c013a738> sys_futex+0x88/0x100  <c0102fbb> sysenter_past_esp+0x54/0x79
[17181648.396000] gthumb        S F7D1D6C0     0  4758      1          4766  4756 (NOTLB)
[17181648.396000]        eeacfe98 00000082 eeacfe60 f7d1d6c0 eeacff38 c0178953 dfab3ec0 f8983170 
[17181648.396000]        9f740600 003d09bd c1a2da98 eeace000 c1a2d8a4 c1a2da98 00000005 ea401668 
[17181648.396000]        ea401560 c1959a90 c1806ce0 9f740600 003d09bd 00000000 00000000 00000044 
[17181648.396000] Call Trace:
[17181648.396000]  <c0178953> do_lookup+0x53/0x160  <f8983170> ext3_permission+0x0/0x10 [ext3]
[17181648.396000]  <c02d9e85> schedule_timeout+0x75/0xc0  <c0139645> get_futex_key+0x45/0x110
[17181648.396000]  <c011cd8f> __wake_up_sync+0x3f/0x70  <c013643d> add_wait_queue+0x1d/0x50
[17181648.396000]  <c013a479> do_futex+0x799/0x9d0  <c011bde0> default_wake_function+0x0/0x10
[17181648.396000]  <c0125988> do_exit+0x498/0x840  <c013a738> sys_futex+0x88/0x100
[17181648.396000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17181648.396000] gthumb        S 00000000     0  4766      1          4767  4758 (NOTLB)
[17181648.396000]        eaabfe98 00000082 02600043 00000000 00000000 00140096 0007003e 02602ac0 
[17181648.396000]        a52cde00 003d09bd 00000000 eaabe000 00140096 00040038 00000001 dfc2e668 
[17181648.396000]        dfc2e560 df931560 c1806ce0 a52cde00 003d09bd 00000000 00000000 0000cf87 
[17181648.396000] Call Trace:
[17181648.396000]  <c015b58d> find_extend_vma+0x1d/0x70  <c02d9e85> schedule_timeout+0x75/0xc0
[17181648.396000]  <c0139645> get_futex_key+0x45/0x110  <c013643d> add_wait_queue+0x1d/0x50
[17181648.396000]  <c013a479> do_futex+0x799/0x9d0  <c013a738> sys_futex+0x88/0x100
[17181648.396000]  <c011bde0> default_wake_function+0x0/0x10  <c015bdd6> do_munmap+0x186/0x1e0
[17181648.396000]  <c013a738> sys_futex+0x88/0x100  <c0102fbb> sysenter_past_esp+0x54/0x79
[17181648.396000] gthumb        S 00000000     0  4767      1          4768  4766 (NOTLB)
[17181648.396000]        eba23e98 00000082 00000000 00000000 00000000 00000000 00000000 00000000 
[17181648.396000]        a52cde00 003d09bd 000002ee eba22000 00000000 00000000 00000001 df931668 
[17181648.396000]        df931560 c1948560 c1806ce0 a52cde00 003d09bd 00000000 00000000 00000000 
[17181648.396000] Call Trace:
[17181648.396000]  <c02d9e85> schedule_timeout+0x75/0xc0  <c0139645> get_futex_key+0x45/0x110
[17181648.396000]  <c013643d> add_wait_queue+0x1d/0x50  <c013a479> do_futex+0x799/0x9d0
[17181648.396000]  <c011bde0> default_wake_function+0x0/0x10  <c013a738> sys_futex+0x88/0x100
[17181648.396000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17181648.396000] gthumb        S 00000001     0  4768      1          4775  4767 (NOTLB)
[17181648.396000]        eba25e98 00000082 00000029 00000001 05f0029e 00000000 00000000 00000000 
[17181648.396000]        a52cde00 003d09bd 00000000 eba24000 00000029 00000001 00000001 c1948668 
[17181648.396000]        c1948560 c1959a90 c1806ce0 a52cde00 003d09bd 00000000 00000000 00000001 
[17181648.396000] Call Trace:
[17181648.396000]  <c02d9e85> schedule_timeout+0x75/0xc0  <c0139645> get_futex_key+0x45/0x110
[17181648.396000]  <c013643d> add_wait_queue+0x1d/0x50  <c013a479> do_futex+0x799/0x9d0
[17181648.396000]  <c011bde0> default_wake_function+0x0/0x10  <c013a738> sys_futex+0x88/0x100
[17181648.396000]  <c0102fbb> sysenter_past_esp+0x54/0x79 

I've got no Idea how to parse them but all of those call traces seem to end to "ysenter_past_esp+0x54/0x79"


After the first time(after reboot) I vaguely remember using hdparm and it showing read (and write?) errors but now I can't remember how I got it to show that stuff.

When these happen, I can't access my second harddisk (which also showed the errors back then with hdparm), /2nddisk/, all that access it go to "Uninterruptible" state and can't be killed.

Also to get the computer working again, I reboot. After reboot everything seem to work fine.


Also a while back (between these two uninterruptiple-scenarios, I tried to burn a dvd with gnomebuster but when it went to 50%, it froze and after killing it and looking at system monitor, there were two cdrecord.mmap process names which were "Uninterruptible". Here's stuff from that time: > Dec 22 11:40:16 kajakki kernel: [17185288.516000] cdrom: This disc doesn't have any tracks I recognize!
Dec 22 11:41:02 kajakki kernel: [17185334.352000] scsi: unknown opcode 0xe9
Dec 22 11:41:02 kajakki kernel: [17185334.352000] scsi: unknown opcode 0xed
Dec 22 11:41:02 kajakki kernel: [17185334.796000] scsi: unknown opcode 0x01
Dec 22 11:41:07 kajakki kernel: [17185339.888000] scsi: unknown opcode 0xf5
Dec 22 11:42:15 kajakki kernel: [17185407.872000] ide-cd: cmd 0x3 timed out
Dec 22 11:42:15 kajakki kernel: [17185407.872000] hda: irq timeout: status=0xd0 { Busy }
Dec 22 11:42:15 kajakki kernel: [17185407.872000] ide: failed opcode was: unknown
Dec 22 11:42:15 kajakki kernel: [17185407.872000] hda: DMA disabled
Dec 22 11:42:15 kajakki kernel: [17185407.920000] hda: ATAPI reset complete
Dec 22 11:43:15 kajakki kernel: [17185467.920000] ide-cd: cmd 0x3 timed out
Dec 22 11:43:15 kajakki kernel: [17185467.920000] hda: irq timeout: status=0x80 { Busy }
Dec 22 11:43:15 kajakki kernel: [17185467.920000] ide: failed opcode was: unknown
Dec 22 11:43:15 kajakki kernel: [17185467.968000] hda: ATAPI reset complete
Dec 22 11:44:20 kajakki kernel: [17185527.968000] ide-cd: cmd 0x3 timed out
Dec 22 11:44:20 kajakki kernel: [17185527.968000] hda: irq timeout: status=0x80 { Busy }
Dec 22 11:44:20 kajakki kernel: [17185527.968000] ide: failed opcode was: unknown
Dec 22 11:44:20 kajakki kernel: [17185532.972000] hda: status timeout: status=0x80 { Busy }
Dec 22 11:44:20 kajakki kernel: [17185532.972000] ide: failed opcode was: unknown
Dec 22 11:44:20 kajakki kernel: [17185532.972000] hda: drive not ready for command
Dec 22 11:44:20 kajakki kernel: [17185533.020000] hda: ATAPI reset complete
Dec 22 11:45:20 kajakki kernel: [17185593.020000] hda: irq timeout: status=0x80 { Busy }
Dec 22 11:45:20 kajakki kernel: [17185593.020000] ide: failed opcode was: unknown
Dec 22 11:45:20 kajakki kernel: [17185593.068000] hda: ATAPI reset complete
Dec 22 11:46:25 kajakki kernel: [17185653.068000] hda: irq timeout: status=0x80 { Busy }
Dec 22 11:46:25 kajakki kernel: [17185653.068000] ide: failed opcode was: unknown
Dec 22 11:46:25 kajakki kernel: [17185658.072000] hda: status timeout: status=0x80 { Busy }
Dec 22 11:46:25 kajakki kernel: [17185658.072000] ide: failed opcode was: unknown
Dec 22 11:46:25 kajakki kernel: [17185658.072000] hda: drive not ready for command
Dec 22 11:46:25 kajakki kernel: [17185658.120000] hda: ATAPI reset complete
Dec 22 12:13:19 kajakki kernel: 56389f8 0000000a c19c6668 


> F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
0  1000  6446     1 -100  -   6168  6168 blk_ex DL   ?          0:00 cdrecord mmap dev=/dev/hda gracetime=5 speed=8 -v -eject -dao -overburn -multi tsize=259051s -pad -
1  1000  6449  6446 -99   -   6168  4712 blk_ex D    ?          0:00  \_ cdrecord mmap dev=/dev/hda gracetime=5 speed=8 -v -eject -dao -overburn -multi tsize=259051s -pad -

> Dec 22 12:13:19 kajakki kernel: [17187271.520000] cdrecord.mmap D CA6F5B6C     0  6446      1  6449    6650  6585 (NOTLB)
Dec 22 12:13:19 kajakki kernel: [17187271.520000]        ca6f5b80 00200082 00000002 ca6f5b6c c048e300 dff24e80 c025238e 0092ac53 
Dec 22 12:13:19 kajakki kernel: [17187271.520000]        8e239900 003d0dfb ffffffff ca6f4000 00000000 0092ac53 00000007 ead37138 
Dec 22 12:13:19 kajakki kernel: [17187271.520000]        ead37030 c03686c0 c1806ce0 8e60a200 003d0dfb 00000000 00000000 00200086 
Dec 22 12:13:19 kajakki kernel: [17187271.520000] Call Trace:
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c025238e> ide_do_request+0x47e/0x8a0  <c01d4bb6> blk_remove_plug+0x26/0x60
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d1845> elv_drain_elevator+0x15/0x60  <c02d975d> wait_for_completion+0x8d/0xd0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c011bde0> default_wake_function+0x0/0x10  <c01d4d51> blk_execute_rq+0x81/0xf0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d42e0> blk_end_sync_rq+0x0/0x20  <c01d8b9d> sg_io+0x1fd/0x350
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f910e9c0> _nv005440rm+0x28/0x44 [nvidia]  <c01d9417> scsi_cmd_ioctl+0x3d7/0x4b0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8f982f1> _nv002668rm+0x1d/0x2c [nvidia]  <f8f982fa> _nv002668rm+0x26/0x2c [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f910e9c0> _nv005440rm+0x28/0x44 [nvidia]  <f910ea87> _nv005438rm+0x23/0x28 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8f982f1> _nv002668rm+0x1d/0x2c [nvidia]  <f8f982f1> _nv002668rm+0x1d/0x2c [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f88c1534> cdrom_ioctl+0x34/0xdd0 [cdrom]  <f910ea87> _nv005438rm+0x23/0x28 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c0265529> pci_read+0x29/0x30  <f910e9c0> _nv005440rm+0x28/0x44 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f88c9f90> idecd_ioctl+0x170/0x180 [ide_cd]  <c01512e2> get_page_from_freelist+0x3a2/0x410
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d6d8d> blkdev_driver_ioctl+0x6d/0x80  <c01d708f> blkdev_ioctl+0x2ef/0x7d0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01513a6> __alloc_pages+0x56/0x330  <c015f16d> anon_vma_prepare+0x1d/0xe0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c0153660> __pagevec_lru_add_active+0xa0/0xc0  <c0157f25> do_wp_page+0x205/0x300
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c015935d> __handle_mm_fault+0x62d/0x900  <c01724b8> block_ioctl+0x18/0x20
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01724a0> block_ioctl+0x0/0x20  <c017d5eb> do_ioctl+0x2b/0x90
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c017d6ac> vfs_ioctl+0x5c/0x2b0  <c012a2fc> __capable+0xc/0x20
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c017d972> sys_ioctl+0x72/0x90  <c0102fbb> sysenter_past_esp+0x54/0x79
Dec 22 12:13:19 kajakki kernel: [17187271.520000] cdrecord.mmap D C8155B18     0  6449   6446                     (NOTLB)
Dec 22 12:13:19 kajakki kernel: [17187271.520000]        c8155b80 00200086 0000002e c8155b18 f8f982fa f785901c 00200082 c8155b38 
Dec 22 12:13:19 kajakki kernel: [17187271.520000]        d09b1100 003d0e3c ffffffff c8154000 00000000 00000010 00000005 c19be668 
Dec 22 12:13:19 kajakki kernel: [17187271.520000]        c19be560 dffaa030 c1806ce0 d09b1100 003d0e3c 00000000 00000000 00000000 
Dec 22 12:13:19 kajakki kernel: [17187271.520000] Call Trace:
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8f982fa> _nv002668rm+0x26/0x2c [nvidia]  <c01d4bb6> blk_remove_plug+0x26/0x60
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d1845> elv_drain_elevator+0x15/0x60  <c02d975d> wait_for_completion+0x8d/0xd0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c011bde0> default_wake_function+0x0/0x10  <c01d4d51> blk_execute_rq+0x81/0xf0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d42e0> blk_end_sync_rq+0x0/0x20  <c01dec30> cfq_set_request+0x0/0x3c0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d16d4> elv_set_request+0x24/0x50  <c01d46db> get_request+0x29b/0x2c0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d4de7> get_request_wait+0x27/0x120  <c01d8b9d> sg_io+0x1fd/0x350
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d9417> scsi_cmd_ioctl+0x3d7/0x4b0  <f910ea87> _nv005438rm+0x23/0x28 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f910ea87> _nv005438rm+0x23/0x28 [nvidia]  <f8f982f1> _nv002668rm+0x1d/0x2c [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8f982fa> _nv002668rm+0x26/0x2c [nvidia]  <f910ea87> _nv005438rm+0x23/0x28 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f88c1534> cdrom_ioctl+0x34/0xdd0 [cdrom]  <f8fafba6> rm_set_interrupts+0x12e/0x164 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8fafbc4> rm_set_interrupts+0x14c/0x164 [nvidia]  <f88c9f90> idecd_ioctl+0x170/0x180 [ide_cd]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8fa78f6> _nv002470rm+0x12/0x18 [nvidia]  <f910ea87> _nv005438rm+0x23/0x28 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <f8fab7bc> _nv001806rm+0x9c/0xa8 [nvidia]  <f8fab7a7> _nv001806rm+0x87/0xa8 [nvidia]
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01d6d8d> blkdev_driver_ioctl+0x6d/0x80  <c01d708f> blkdev_ioctl+0x2ef/0x7d0
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c011aca4> __activate_task+0x14/0x30  <c014ba30> find_get_page+0x20/0x50
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c014ebf3> filemap_nopage+0x2f3/0x3a0  <c0157f25> do_wp_page+0x205/0x300
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c0158f41> __handle_mm_fault+0x211/0x900  <c01724b8> block_ioctl+0x18/0x20
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c01724a0> block_ioctl+0x0/0x20  <c017d5eb> do_ioctl+0x2b/0x90
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c017d6ac> vfs_ioctl+0x5c/0x2b0  <c012a2fc> __capable+0xc/0x20
Dec 22 12:13:19 kajakki kernel: [17187271.520000]  <c017d972> sys_ioctl+0x72/0x90  <c0102fbb> sysenter_past_esp+0x54/0x79

And the same "sysenter_past_esp+0x54/0x79" ghost here.


I'm totally clueless. HELP PLEASE !

And ofcourse I forgot to add that those two harddisks are brand-new (bought two weeks ago).

---

