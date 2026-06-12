---
title: "Kernel Panic"
date: 2022-11-21
forum: Hardware
---

### Post by duggers on 2022-11-21
Hi All,

I've been seeing these panic logs periodically and it's also been halting the system. I do suspect the Intel Pro adapter but don't see in the log anything that I can identify that relates to a device, though I see entries relating to raid, I have Adaptec RAID 6 on this server. I would have thought that since it is hardware RAID, it would simply present as a regular volume and there would be no kernel involvement, but looking at these logs that's definitely not the case. Can anyone see what's causing the crashes I'm seeing?

Thanks for reading
Ian



Nov 21 04:24:25 linuxserver kernel: [39346.704315] aacraid: Host bus reset request. SCSI hang ?
Nov 21 04:24:25 linuxserver kernel: [39346.704497] aacraid 0000:02:00.0: Adapter health - 5
Nov 21 04:24:25 linuxserver kernel: [39346.704654] aacraid 0000:02:00.0: outstanding cmd: midlevel-0
Nov 21 04:24:25 linuxserver kernel: [39346.704656] aacraid 0000:02:00.0: outstanding cmd: lowlevel-0
Nov 21 04:24:25 linuxserver kernel: [39346.704658] aacraid 0000:02:00.0: outstanding cmd: error handler-0
Nov 21 04:24:25 linuxserver kernel: [39346.704659] aacraid 0000:02:00.0: outstanding cmd: firmware-2
Nov 21 04:24:25 linuxserver kernel: [39346.704661] aacraid 0000:02:00.0: outstanding cmd: kernel-0
Nov 21 04:24:25 linuxserver kernel: [39346.728243] ------------[ cut here ]------------
Nov 21 04:24:25 linuxserver kernel: [39346.728246] refcount_t: addition on 0; use-after-free.
Nov 21 04:24:25 linuxserver kernel: [39346.728260] WARNING: CPU: 6 PID: 270 at lib/refcount.c:25 refcount_warn_saturate+0x9f/0x150
Nov 21 04:24:25 linuxserver kernel: [39346.728271] Modules linked in: vhost_net vhost vhost_iotlb tap xt_CHECKSUM xt_MASQUERADE bridge stp llc ip6t_REJECT xt_hl ip6_tables ip6t_rt ipt_REJECT xt_LOG nf_log_syslo>
Nov 21 04:24:25 linuxserver kernel: [39346.728354]  pstore_blk pstore_zone efi_pstore ip_tables x_tables autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c >
Nov 21 04:24:25 linuxserver kernel: [39346.728407] CPU: 6 PID: 270 Comm: scsi_eh_0 Not tainted 5.15.0-53-generic #59-Ubuntu
Nov 21 04:24:25 linuxserver kernel: [39346.728411] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./EPC612D8A, BIOS 5.11 03/21/2017
Nov 21 04:24:25 linuxserver kernel: [39346.728413] RIP: 0010:refcount_warn_saturate+0x9f/0x150
Nov 21 04:24:25 linuxserver kernel: [39346.728417] Code: cc cc 0f b6 1d 21 51 ba 01 80 fb 01 0f 87 36 79 6e 00 83 e3 01 75 e1 48 c7 c7 28 46 83 a9 c6 05 05 51 ba 01 01 e8 b8 fe 6a 00 <0f> 0b eb ca 0f b6 1d f7 5>
Nov 21 04:24:25 linuxserver kernel: [39346.728420] RSP: 0018:ffffa31000dffcd8 EFLAGS: 00010286
Nov 21 04:24:25 linuxserver kernel: [39346.728423] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000000027
Nov 21 04:24:25 linuxserver kernel: [39346.728425] RDX: ffff8ca1ffda0588 RSI: 0000000000000001 RDI: ffff8ca1ffda0580
Nov 21 04:24:25 linuxserver kernel: [39346.728428] RBP: ffffa31000dffce0 R08: 0000000000000003 R09: fffffffffffda370
Nov 21 04:24:25 linuxserver kernel: [39346.728429] R10: 000000000000002c R11: 0000000000000001 R12: ffff8c92c5da6400
Nov 21 04:24:25 linuxserver kernel: [39346.728431] R13: ffff8c92c5da6428 R14: ffff8c92dbbf0000 R15: 0000000000000002
Nov 21 04:24:25 linuxserver kernel: [39346.728433] FS:  0000000000000000(0000) GS:ffff8ca1ffd80000(0000) knlGS:0000000000000000
Nov 21 04:24:25 linuxserver kernel: [39346.728436] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 21 04:24:25 linuxserver kernel: [39346.728438] CR2: 00007fbd9af17830 CR3: 00000003ac010004 CR4: 00000000001726e0
Nov 21 04:24:25 linuxserver kernel: [39346.728441] Call Trace:
Nov 21 04:24:25 linuxserver kernel: [39346.728443]  <TASK>
Nov 21 04:24:25 linuxserver kernel: [39346.728447]  kthread_stop+0x15f/0x170
Nov 21 04:24:25 linuxserver kernel: [39346.728456]  _aac_reset_adapter+0x2fa/0x450 [aacraid]
Nov 21 04:24:25 linuxserver kernel: [39346.728468]  ? scsi_host_block+0xc0/0xf0
Nov 21 04:24:25 linuxserver kernel: [39346.728475]  aac_reset_adapter+0x9c/0x210 [aacraid]
Nov 21 04:24:25 linuxserver kernel: [39346.728484]  aac_eh_host_reset+0x64/0xf0 [aacraid]
Nov 21 04:24:25 linuxserver kernel: [39346.728491]  scsi_try_host_reset+0x43/0xf0
Nov 21 04:24:25 linuxserver kernel: [39346.728494]  scsi_eh_ready_devs+0xc5/0x240
Nov 21 04:24:25 linuxserver kernel: [39346.728498]  scsi_unjam_host+0x105/0x1c0
Nov 21 04:24:25 linuxserver kernel: [39346.728502]  scsi_error_handler+0x13d/0x180
Nov 21 04:24:25 linuxserver kernel: [39346.728505]  ? scsi_unjam_host+0x1c0/0x1c0
Nov 21 04:24:25 linuxserver kernel: [39346.728508]  kthread+0x12a/0x150
Nov 21 04:24:25 linuxserver kernel: [39346.728513]  ? set_kthread_struct+0x50/0x50
Nov 21 04:24:25 linuxserver kernel: [39346.728518]  ret_from_fork+0x22/0x30
Nov 21 04:24:25 linuxserver kernel: [39346.728525]  </TASK>
Nov 21 04:24:25 linuxserver kernel: [39346.728526] ---[ end trace 197daad0c2fc28bf ]---
Nov 21 04:24:25 linuxserver kernel: [39346.728529] ------------[ cut here ]------------
Nov 21 04:24:25 linuxserver kernel: [39346.728531] refcount_t: underflow; use-after-free.
Nov 21 04:24:25 linuxserver kernel: [39346.728538] WARNING: CPU: 6 PID: 270 at lib/refcount.c:28 refcount_warn_saturate+0xf7/0x150
Nov 21 04:24:25 linuxserver kernel: [39346.728543] Modules linked in: vhost_net vhost vhost_iotlb tap xt_CHECKSUM xt_MASQUERADE bridge stp llc ip6t_REJECT xt_hl ip6_tables ip6t_rt ipt_REJECT xt_LOG nf_log_syslo>
Nov 21 04:24:25 linuxserver kernel: [39346.728610]  pstore_blk pstore_zone efi_pstore ip_tables x_tables autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c >
Nov 21 04:24:25 linuxserver kernel: [39346.728652] CPU: 6 PID: 270 Comm: scsi_eh_0 Tainted: G        W         5.15.0-53-generic #59-Ubuntu
Nov 21 04:24:25 linuxserver kernel: [39346.728655] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./EPC612D8A, BIOS 5.11 03/21/2017
Nov 21 04:24:25 linuxserver kernel: [39346.728657] RIP: 0010:refcount_warn_saturate+0xf7/0x150
Nov 21 04:24:25 linuxserver kernel: [39346.728660] Code: eb 9e 0f b6 1d c8 50 ba 01 80 fb 01 0f 87 06 79 6e 00 83 e3 01 75 89 48 c7 c7 58 46 83 a9 c6 05 ac 50 ba 01 01 e8 60 fe 6a 00 <0f> 0b e9 6f ff ff ff 0f b>
Nov 21 04:24:25 linuxserver kernel: [39346.728662] RSP: 0018:ffffa31000dffcd8 EFLAGS: 00010286
Nov 21 04:24:25 linuxserver kernel: [39346.728665] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000000027
Nov 21 04:24:25 linuxserver kernel: [39346.728667] RDX: ffff8ca1ffda0588 RSI: 0000000000000001 RDI: ffff8ca1ffda0580
Nov 21 04:24:25 linuxserver kernel: [39346.728669] RBP: ffffa31000dffce0 R08: 0000000000000003 R09: fffffffffffdb170
Nov 21 04:24:25 linuxserver kernel: [39346.728670] R10: 0000000000000028 R11: 0000000000000001 R12: ffff8c92c5da6400
Nov 21 04:24:25 linuxserver kernel: [39346.728672] R13: ffff8c92c5da6428 R14: 0000000000000000 R15: 0000000000000002
Nov 21 04:24:25 linuxserver kernel: [39346.728674] FS:  0000000000000000(0000) GS:ffff8ca1ffd80000(0000) knlGS:0000000000000000
Nov 21 04:24:25 linuxserver kernel: [39346.728676] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 21 04:24:25 linuxserver kernel: [39346.728678] CR2: 00007fbd9af17830 CR3: 00000003ac010004 CR4: 00000000001726e0
Nov 21 04:24:25 linuxserver kernel: [39346.728680] Call Trace:
Nov 21 04:24:25 linuxserver kernel: [39346.728681]  <TASK>
Nov 21 04:24:25 linuxserver kernel: [39346.728683]  kthread_stop+0x14d/0x170
Nov 21 04:24:25 linuxserver kernel: [39346.728688]  _aac_reset_adapter+0x2fa/0x450 [aacraid]
Nov 21 04:24:25 linuxserver kernel: [39346.728696]  ? scsi_host_block+0xc0/0xf0
Nov 21 04:24:25 linuxserver kernel: [39346.728700]  aac_reset_adapter+0x9c/0x210 [aacraid]
Nov 21 04:24:25 linuxserver kernel: [39346.728708]  aac_eh_host_reset+0x64/0xf0 [aacraid]
Nov 21 04:24:25 linuxserver kernel: [39346.728715]  scsi_try_host_reset+0x43/0xf0
Nov 21 04:24:25 linuxserver kernel: [39346.728718]  scsi_eh_ready_devs+0xc5/0x240
Nov 21 04:24:25 linuxserver kernel: [39346.728722]  scsi_unjam_host+0x105/0x1c0
Nov 21 04:24:25 linuxserver kernel: [39346.728725]  scsi_error_handler+0x13d/0x180
Nov 21 04:24:25 linuxserver kernel: [39346.728728]  ? scsi_unjam_host+0x1c0/0x1c0
Nov 21 04:24:25 linuxserver kernel: [39346.728732]  kthread+0x12a/0x150
Nov 21 04:24:25 linuxserver kernel: [39346.728736]  ? set_kthread_struct+0x50/0x50
Nov 21 04:24:25 linuxserver kernel: [39346.728741]  ret_from_fork+0x22/0x30
Nov 21 04:24:25 linuxserver kernel: [39346.728747]  </TASK>
Nov 21 04:24:25 linuxserver kernel: [39346.728748] ---[ end trace 197daad0c2fc28c0 ]---
Nov 21 04:24:25 linuxserver kernel: [39346.728751] aacraid 0000:02:00.0: Controller reset type is 3
Nov 21 04:24:25 linuxserver kernel: [39346.728935] aacraid 0000:02:00.0: Issuing IOP reset
Nov 21 04:25:05 linuxserver kernel: [39386.542968] aacraid 0000:02:00.0: IOP reset succeeded
Nov 21 04:25:07 linuxserver kernel: [39388.559945] aacraid: Comm Interface type1 enabled
Nov 21 04:25:18 linuxserver kernel: [39399.285833] aacraid 0000:02:00.0: Scheduling bus rescan
Nov 21 04:41:47 linuxserver kernel: [40387.902516] general protection fault, probably for non-canonical address 0x12a9752c3d944f50: 0000 [#1] SMP PTI
Nov 21 04:41:47 linuxserver kernel: [40387.902847] CPU: 4 PID: 4883 Comm: smbd Tainted: G        W         5.15.0-53-generic #59-Ubuntu
Nov 21 04:41:47 linuxserver kernel: [40387.903130] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./EPC612D8A, BIOS 5.11 03/21/2017
Nov 21 04:41:47 linuxserver kernel: [40387.903431] RIP: 0010:__kmalloc+0x111/0x330
Nov 21 04:41:47 linuxserver kernel: [40387.903570] Code: 8b 50 08 49 8b 00 49 83 78 10 00 48 89 45 c8 0f 84 c5 01 00 00 48 85 c0 0f 84 bc 01 00 00 41 8b 4c 24 28 49 8b 3c 24 48 01 c1 <48> 8b 19 48 89 ce 49 33 9>
Nov 21 04:41:47 linuxserver kernel: [40387.904162] RSP: 0018:ffffa31001f33b28 EFLAGS: 00010206
Nov 21 04:41:47 linuxserver kernel: [40387.904331] RAX: 12a9752c3d944f10 RBX: 0000000000000dc0 RCX: 12a9752c3d944f50
Nov 21 04:41:47 linuxserver kernel: [40387.904557] RDX: 00000000000428be RSI: 0000000000000dc0 RDI: 00000000000350e0
Nov 21 04:41:47 linuxserver kernel: [40387.904784] RBP: ffffa31001f33b68 R08: ffff8ca1ffd350e0 R09: 0000000019003c4e
Nov 21 04:41:47 linuxserver kernel: [40387.905012] R10: 0000000083086118 R11: 0000000002020202 R12: ffff8c92c0042700
Nov 21 04:41:47 linuxserver kernel: [40387.905238] R13: ffffffffa8666aae R14: 0000000000000dc0 R15: 0000000000000000
Nov 21 04:41:47 linuxserver kernel: [40387.905465] FS:  00007f65e696aa40(0000) GS:ffff8ca1ffd00000(0000) knlGS:0000000000000000
Nov 21 04:41:47 linuxserver kernel: [40387.905723] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 21 04:41:47 linuxserver kernel: [40387.905904] CR2: 00007fe6196af4e9 CR3: 0000000296974004 CR4: 00000000001726e0
Nov 21 04:41:47 linuxserver kernel: [40387.906132] Call Trace:
Nov 21 04:41:47 linuxserver kernel: [40387.906211]  <TASK>
Nov 21 04:41:47 linuxserver kernel: [40387.906279]  ext4_htree_store_dirent+0x3e/0x110
Nov 21 04:41:47 linuxserver kernel: [40387.906429]  htree_dirblock_to_tree+0x1f2/0x3a0
Nov 21 04:41:47 linuxserver kernel: [40387.906577]  ? sock_recvmsg+0x71/0x80
Nov 21 04:41:47 linuxserver kernel: [40387.906697]  ext4_htree_fill_tree+0x28a/0x410
Nov 21 04:41:47 linuxserver kernel: [40387.906837]  ext4_dx_readdir+0x151/0x430
Nov 21 04:41:47 linuxserver kernel: [40387.906964]  ext4_readdir+0x76/0x810
Nov 21 04:41:47 linuxserver kernel: [40387.907098]  ? fsnotify_perm.part.0+0x11b/0x160
Nov 21 04:41:47 linuxserver kernel: [40387.907244]  iterate_dir+0xa2/0x1d0
Nov 21 04:41:47 linuxserver kernel: [40387.907359]  __x64_sys_getdents64+0x80/0x120
Nov 21 04:41:47 linuxserver kernel: [40387.907494]  ? __ia32_sys_getdents+0x120/0x120
Nov 21 04:41:47 linuxserver kernel: [40387.907636]  do_syscall_64+0x5c/0xc0
Nov 21 04:41:47 linuxserver kernel: [40387.907753]  ? exit_to_user_mode_prepare+0x96/0xb0
Nov 21 04:41:47 linuxserver kernel: [40387.907908]  ? syscall_exit_to_user_mode+0x27/0x50
Nov 21 04:41:47 linuxserver kernel: [40387.908063]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:47 linuxserver kernel: [40387.913506]  ? syscall_exit_to_user_mode+0x27/0x50
Nov 21 04:41:47 linuxserver kernel: [40387.919003]  ? __x64_sys_close+0x11/0x50
Nov 21 04:41:47 linuxserver kernel: [40387.924495]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:47 linuxserver kernel: [40387.929810]  ? sysvec_apic_timer_interrupt+0x4e/0x90
Nov 21 04:41:47 linuxserver kernel: [40387.935022]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
Nov 21 04:41:47 linuxserver kernel: [40387.940147] RIP: 0033:0x7f65eab886b7
Nov 21 04:41:47 linuxserver kernel: [40387.945113] Code: ac fa ff 4c 89 e0 5b 5d 41 5c c3 0f 1f 84 00 00 00 00 00 f3 0f 1e fa b8 ff ff ff 7f 48 39 c2 48 0f 47 d0 b8 d9 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 01 c>
Nov 21 04:41:47 linuxserver kernel: [40387.960447] RSP: 002b:00007ffc09432308 EFLAGS: 00000293 ORIG_RAX: 00000000000000d9
Nov 21 04:41:47 linuxserver kernel: [40387.965606] RAX: ffffffffffffffda RBX: 000055851a8733b0 RCX: 00007f65eab886b7
Nov 21 04:41:47 linuxserver kernel: [40387.965610] RDX: 0000000000008000 RSI: 000055851a8733b0 RDI: 000000000000002f
Nov 21 04:41:47 linuxserver kernel: [40387.965612] RBP: 000055851a873384 R08: 00007ffc09432470 R09: 0000000000000001
Nov 21 04:41:47 linuxserver kernel: [40387.965612] RBP: 000055851a873384 R08: 00007ffc09432470 R09: 0000000000000001
Nov 21 04:41:47 linuxserver kernel: [40387.965615] R10: 0000000000000000 R11: 0000000000000293 R12: ffffffffffffff58
Nov 21 04:41:47 linuxserver kernel: [40387.965617] R13: 0000000000000000 R14: 000055851a873380 R15: 000055851a63f2a0
Nov 21 04:41:47 linuxserver kernel: [40387.965622]  </TASK>
Nov 21 04:41:47 linuxserver kernel: [40387.995627] Modules linked in: vhost_net vhost vhost_iotlb tap xt_CHECKSUM xt_MASQUERADE bridge stp llc ip6t_REJECT xt_hl ip6_tables ip6t_rt ipt_REJECT xt_LOG nf_log_syslo>
Nov 21 04:41:47 linuxserver kernel: [40387.995763]  pstore_blk pstore_zone efi_pstore ip_tables x_tables autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c >
Nov 21 04:41:47 linuxserver kernel: [40388.094068] ---[ end trace 197daad0c2fc28c1 ]---
Nov 21 04:41:47 linuxserver kernel: [40388.599658] RIP: 0010:__kmalloc+0x111/0x330
Nov 21 04:41:47 linuxserver kernel: [40388.606931] Code: 8b 50 08 49 8b 00 49 83 78 10 00 48 89 45 c8 0f 84 c5 01 00 00 48 85 c0 0f 84 bc 01 00 00 41 8b 4c 24 28 49 8b 3c 24 48 01 c1 <48> 8b 19 48 89 ce 49 33 9>
Nov 21 04:41:47 linuxserver kernel: [40388.629755] RSP: 0018:ffffa31001f33b28 EFLAGS: 00010206
Nov 21 04:41:47 linuxserver kernel: [40388.637521] RAX: 12a9752c3d944f10 RBX: 0000000000000dc0 RCX: 12a9752c3d944f50
Nov 21 04:41:47 linuxserver kernel: [40388.645422] RDX: 00000000000428be RSI: 0000000000000dc0 RDI: 00000000000350e0
Nov 21 04:41:47 linuxserver kernel: [40388.653320] RBP: ffffa31001f33b68 R08: ffff8ca1ffd350e0 R09: 0000000019003c4e
Nov 21 04:41:47 linuxserver kernel: [40388.661240] R10: 0000000083086118 R11: 0000000002020202 R12: ffff8c92c0042700
Nov 21 04:41:47 linuxserver kernel: [40388.669171] R13: ffffffffa8666aae R14: 0000000000000dc0 R15: 0000000000000000
Nov 21 04:41:47 linuxserver kernel: [40388.677028] FS:  00007f65e696aa40(0000) GS:ffff8ca1ffd00000(0000) knlGS:0000000000000000
Nov 21 04:41:47 linuxserver kernel: [40388.684829] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 21 04:41:47 linuxserver kernel: [40388.692547] CR2: 00007fe6196af4e9 CR3: 0000000296974004 CR4: 00000000001726e0
Nov 21 04:41:50 linuxserver kernel: [40391.238209] general protection fault, probably for non-canonical address 0x12a9752c3d944f50: 0000 [#2] SMP PTI
Nov 21 04:41:50 linuxserver kernel: [40391.253782] CPU: 4 PID: 63687 Comm: smbd Tainted: G      D W         5.15.0-53-generic #59-Ubuntu
Nov 21 04:41:50 linuxserver kernel: [40391.261893] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./EPC612D8A, BIOS 5.11 03/21/2017
Nov 21 04:41:50 linuxserver kernel: [40391.278188] RIP: 0010:__kmalloc+0x111/0x330
Nov 21 04:41:50 linuxserver kernel: [40391.286342] Code: 8b 50 08 49 8b 00 49 83 78 10 00 48 89 45 c8 0f 84 c5 01 00 00 48 85 c0 0f 84 bc 01 00 00 41 8b 4c 24 28 49 8b 3c 24 48 01 c1 <48> 8b 19 48 89 ce 49 33 9>
Nov 21 04:41:50 linuxserver kernel: [40391.310949] RSP: 0018:ffffa31009eefaf8 EFLAGS: 00010206
Nov 21 04:41:50 linuxserver kernel: [40391.319002] RAX: 12a9752c3d944f10 RBX: 0000000000000dc0 RCX: 12a9752c3d944f50
Nov 21 04:41:50 linuxserver kernel: [40391.327031] RDX: 00000000000428be RSI: 0000000000000dc0 RDI: 00000000000350e0
Nov 21 04:41:50 linuxserver kernel: [40391.334916] RBP: ffffa31009eefb38 R08: ffff8ca1ffd350e0 R09: 00000000e02f54e6
Nov 21 04:41:50 linuxserver kernel: [40391.334920] R10: 0000000000a46410 R11: 0000000002020202 R12: ffff8c92c0042700
Nov 21 04:41:50 linuxserver kernel: [40391.334923] R13: ffffffffa8666aae R14: 0000000000000dc0 R15: 0000000000000000
Nov 21 04:41:50 linuxserver kernel: [40391.334925] FS:  00007f65e696aa40(0000) GS:ffff8ca1ffd00000(0000) knlGS:0000000000000000
Nov 21 04:41:50 linuxserver kernel: [40391.334929] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 21 04:41:50 linuxserver kernel: [40391.334931] CR2: 00000000230c0000 CR3: 0000000151e4a003 CR4: 00000000001726e0
Nov 21 04:41:50 linuxserver kernel: [40391.334934] Call Trace:
Nov 21 04:41:50 linuxserver kernel: [40391.334937]  <TASK>
Nov 21 04:41:50 linuxserver kernel: [40391.334942]  ext4_htree_store_dirent+0x3e/0x110
Nov 21 04:41:50 linuxserver kernel: [40391.334953]  htree_dirblock_to_tree+0x1f2/0x3a0
Nov 21 04:41:50 linuxserver kernel: [40391.334960]  ? ext4_htree_store_dirent+0xf2/0x110
Nov 21 04:41:50 linuxserver kernel: [40391.334965]  ext4_htree_fill_tree+0x28a/0x410
Nov 21 04:41:50 linuxserver kernel: [40391.334971]  ext4_dx_readdir+0x151/0x430
Nov 21 04:41:50 linuxserver kernel: [40391.334976]  ext4_readdir+0x76/0x810
Nov 21 04:41:50 linuxserver kernel: [40391.334981]  ? fsnotify_perm.part.0+0x11b/0x160
Nov 21 04:41:50 linuxserver kernel: [40391.334987]  iterate_dir+0xa2/0x1d0
Nov 21 04:41:50 linuxserver kernel: [40391.334994]  __x64_sys_getdents64+0x80/0x120
Nov 21 04:41:50 linuxserver kernel: [40391.334997]  ? __ia32_sys_getdents+0x120/0x120
Nov 21 04:41:50 linuxserver kernel: [40391.335001]  do_syscall_64+0x5c/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335007]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335010]  ? exit_to_user_mode_prepare+0x37/0xb0
Nov 21 04:41:50 linuxserver kernel: [40391.335016]  ? syscall_exit_to_user_mode+0x27/0x50
Nov 21 04:41:50 linuxserver kernel: [40391.335022]  ? __x64_sys_listxattr+0x1f/0x30
Nov 21 04:41:50 linuxserver kernel: [40391.335028]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335031]  ? syscall_exit_to_user_mode+0x27/0x50
Nov 21 04:41:50 linuxserver kernel: [40391.335035]  ? __x64_sys_newfstatat+0x1c/0x30
Nov 21 04:41:50 linuxserver kernel: [40391.335041]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335045]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335045]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335047]  ? do_syscall_64+0x69/0xc0
Nov 21 04:41:50 linuxserver kernel: [40391.335051]  entry_SYSCALL_64_after_hwframe+0x61/0xcb
Nov 21 04:41:50 linuxserver kernel: [40391.335057] RIP: 0033:0x7f65eab886b7
Nov 21 04:41:50 linuxserver kernel: [40391.335062] Code: ac fa ff 4c 89 e0 5b 5d 41 5c c3 0f 1f 84 00 00 00 00 00 f3 0f 1e fa b8 ff ff ff 7f 48 39 c2 48 0f 47 d0 b8 d9 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 01 c>
Nov 21 04:41:50 linuxserver kernel: [40391.335064] RSP: 002b:00007ffc09432338 EFLAGS: 00000293 ORIG_RAX: 00000000000000d9
Nov 21 04:41:50 linuxserver kernel: [40391.335069] RAX: ffffffffffffffda RBX: 000055851a65a4b0 RCX: 00007f65eab886b7
Nov 21 04:41:50 linuxserver kernel: [40391.335071] RDX: 0000000000008000 RSI: 000055851a65a4b0 RDI: 000000000000002f
Nov 21 04:41:50 linuxserver kernel: [40391.335073] RBP: 000055851a65a484 R08: 00007ffc094324a0 R09: 0000000000000001
Nov 21 04:41:50 linuxserver kernel: [40391.335075] R10: 00007f65eb248a2c R11: 0000000000000293 R12: ffffffffffffff58
Nov 21 04:41:50 linuxserver kernel: [40391.335079] R13: 000000000000003d R14: 000055851a65a480 R15: 000055851a614570
Nov 21 04:41:50 linuxserver kernel: [40391.335083]  </TASK>
Nov 21 04:41:50 linuxserver kernel: [40391.335085] Modules linked in: vhost_net vhost vhost_iotlb tap xt_CHECKSUM xt_MASQUERADE bridge stp llc ip6t_REJECT xt_hl ip6_tables ip6t_rt ipt_REJECT xt_LOG nf_log_syslo>
Nov 21 04:41:50 linuxserver kernel: [40391.335181]  pstore_blk pstore_zone efi_pstore ip_tables x_tables autofs4 raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c >
Nov 21 04:41:50 linuxserver kernel: [40391.335290] ---[ end trace 197daad0c2fc28c2 ]---
Nov 21 04:41:50 linuxserver kernel: [40391.400289] RIP: 0010:__kmalloc+0x111/0x330
Nov 21 04:41:50 linuxserver kernel: [40391.400306] Code: 8b 50 08 49 8b 00 49 83 78 10 00 48 89 45 c8 0f 84 c5 01 00 00 48 85 c0 0f 84 bc 01 00 00 41 8b 4c 24 28 49 8b 3c 24 48 01 c1 <48> 8b 19 48 89 ce 49 33 9>
Nov 21 04:41:50 linuxserver kernel: [40391.400310] RSP: 0018:ffffa31001f33b28 EFLAGS: 00010206
Nov 21 04:41:50 linuxserver kernel: [40391.400319] RAX: 12a9752c3d944f10 RBX: 0000000000000dc0 RCX: 12a9752c3d944f50
Nov 21 04:41:50 linuxserver kernel: [40391.400321] RDX: 00000000000428be RSI: 0000000000000dc0 RDI: 00000000000350e0
Nov 21 04:41:50 linuxserver kernel: [40391.400323] RBP: ffffa31001f33b68 R08: ffff8ca1ffd350e0 R09: 0000000019003c4e
Nov 21 04:41:50 linuxserver kernel: [40391.400326] R10: 0000000083086118 R11: 0000000002020202 R12: ffff8c92c0042700
Nov 21 04:41:50 linuxserver kernel: [40391.400328] R13: ffffffffa8666aae R14: 0000000000000dc0 R15: 0000000000000000
Nov 21 04:41:50 linuxserver kernel: [40391.400331] FS:  00007f65e696aa40(0000) GS:ffff8ca1ffd00000(0000) knlGS:0000000000000000
Nov 21 04:41:50 linuxserver kernel: [40391.400334] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 21 04:41:50 linuxserver kernel: [40391.400336] CR2: 00000000230c0000 CR3: 0000000151e4a003 CR4: 00000000001726e0
Nov 21 04:41:53 linuxserver kernel: [40394.571491] general protection fault, probably for non-canonical address 0x12a9752c3d944f50: 0000 [#3] SMP PTI
Nov 21 04:41:53 linuxserver kernel: [40394.586934] CPU: 4 PID: 63691 Comm: smbd Tainted: G      D W         5.15.0-53-generic #59-Ubuntu
Nov 21 04:41:53 linuxserver kernel: [40394.594991] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./EPC612D8A, BIOS 5.11 03/21/2017
Nov 21 04:41:53 linuxserver kernel: [40394.594994] RIP: 0010:__kmalloc+0x111/0x330
Nov 21 04:41:53 linuxserver kernel: [40394.595005] Code: 8b 50 08 49 8b 00 49 83 78 10 00 48 89 45 c8 0f 84 c5 01 00 00 48 85 c0 0f 84 bc 01 00 00 41 8b 4c 24 28 49 8b 3c 24 48 01 c1 <48> 8b 19 48 89 ce 49 33 9>
Nov 21 04:41:53 linuxserver kernel: [40394.595008] RSP: 0018:ffffa3100a1efb28 EFLAGS: 00010206
Nov 21 04:41:53 linuxserver kernel: [40394.643562] RAX: 12a9752c3d944f10 RBX: 0000000000000dc0 RCX: 12a9752c3d944f50
Nov 21 04:41:53 linuxserver kernel: [40394.643570] RDX: 00000000000428be RSI: 0000000000000dc0 RDI: 00000000000350e0
Nov 21 04:41:53 linuxserver kernel: [40394.643573] RBP: ffffa3100a1efb68 R08: ffff8ca1ffd350e0 R09: 00000000e02f54e6
Nov 21 04:41:53 linuxserver kernel: [40394.674890] R10: 0000000000a46410 R11: 0000000002020202 R12: ffff8c92c0042700
Nov 21 04:41:53 linuxserver kernel: [40394.674895] R13: ffffffffa8666aae R14: 0000000000000dc0 R15: 0000000000000000
Nov 21 04:41:53 linuxserver kernel: [40394.674898] FS:  Nov 21 07:29:44 linuxserver kernel: [    0.000000] microcode: microcode updated early to revision 0x49, date = 2021-08-11

---

