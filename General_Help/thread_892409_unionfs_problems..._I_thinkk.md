---
title: "unionfs problems... I thinkk"
date: 2008-08-17
forum: General Help
---

### Post by craig.francis on 2008-08-17
I've been trying to build a new server (got lots already), but this one keeps puzzling me.

Started off installing CentOS (derivative of RedHat), and it would only remain active for about 2 days before kernel panicking.

I've since replaced pretty much all of the hardware (last bit to go will be the network card).

But during this debugging, I've been using Unbuntu as a boot CD.

The server is trying to mirror a second server, so its main job is to synchronise the data, and that seems to be where most of the problems are, I think (CentOS kernel panics tended to be along the lines of ext3).

With ubuntu, they seem to be "unionfs" related... although I'm sure the disks are formatted as "ext3", or am I getting mixed up?

I've done a bit of research, but can't seem to find anything relating to the following errors... amazingly though, these errors came up, but the server continued working (so was able to scp them off).

------------------------------------

Aug 10 06:47:04 ubuntu kernel: [32950.771122] Unable to handle kernel NULL pointer dereference at 00000000000000f8 RIP: 
Aug 10 06:47:04 ubuntu kernel: [32950.771134]  [unionfs:unionfs_file_revalidate+0x447/0x9b0] :unionfs:unionfs_file_revalidate+0x447/0x9b0
Aug 10 06:47:04 ubuntu kernel: [32950.771151] PGD 3c7bb067 PUD 3ae57067 PMD 0 
Aug 10 06:47:04 ubuntu kernel: [32950.771159] Oops: 0000 [1] SMP 
Aug 10 06:47:04 ubuntu kernel: [32950.771165] CPU 1 
Aug 10 06:47:04 ubuntu kernel: [32950.771169] Modules linked in: ext3 jbd mbcache ipv6 radeon drm af_packet rfcomm l2cap bluetooth ppdev lp powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video output sbs sbshc container dock ac iptable_filter ip_tables x_tables parport_pc parport button i2c_piix4 evdev k8temp i2c_core shpchp pci_hotplug pcspkr battery squashfs loop unionfs nls_cp437 isofs sg ide_cd cdrom sd_mod pata_atiixp pata_acpi ata_generic r8169 via_rhine mii ahci atiixp ide_core libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor fuse
Aug 10 06:47:04 ubuntu kernel: [32950.771279] Pid: 9582, comm: mandb Not tainted 2.6.24-19-generic #1
Aug 10 06:47:04 ubuntu kernel: [32950.771286] RIP: 0010:[unionfs:unionfs_file_revalidate+0x447/0x9b0]  [unionfs:unionfs_file_revalidate+0x447/0x9b0] :unionfs:unionfs_file_revalidate+0x447/0x9b0
Aug 10 06:47:04 ubuntu kernel: [32950.771305] RSP: 0018:ffff810022659e98  EFLAGS: 00010202
Aug 10 06:47:04 ubuntu kernel: [32950.771312] RAX: 0000000000000000 RBX: ffff810039e21d80 RCX: 0000000000000000
Aug 10 06:47:04 ubuntu kernel: [32950.771320] RDX: ffff81003acc31c0 RSI: 0000000000000000 RDI: ffff810039e21d80
Aug 10 06:47:04 ubuntu kernel: [32950.771327] RBP: ffff81003d45a600 R08: 0000000000000000 R09: ffff810022659dc8
Aug 10 06:47:04 ubuntu kernel: [32950.771335] R10: 0000000000000000 R11: 0000000000000246 R12: ffff81003c4b8480
Aug 10 06:47:04 ubuntu kernel: [32950.771343] R13: 0000000000000001 R14: ffff81003c4b8480 R15: ffff81003cf0c820
Aug 10 06:47:04 ubuntu kernel: [32950.771351] FS:  00007fb1fb3136e0(0000) GS:ffff81003d001700(0000) knlGS:0000000000000000
Aug 10 06:47:04 ubuntu kernel: [32950.771363] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 10 06:47:04 ubuntu kernel: [32950.771370] CR2: 00000000000000f8 CR3: 00000000262ed000 CR4: 00000000000006e0
Aug 10 06:47:04 ubuntu kernel: [32950.771378] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 10 06:47:04 ubuntu kernel: [32950.771385] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 10 06:47:04 ubuntu kernel: [32950.771393] Process mandb (pid: 9582, threadinfo ffff810022658000, task ffff81003bd737a0)
Aug 10 06:47:04 ubuntu kernel: [32950.771404] Stack:  0000000122659ec8 ffff81003db88000 ffff810022659ee0 0000000000000001
Aug 10 06:47:04 ubuntu kernel: [32950.771421]  0000000000000008 01ff81003b53e700 0000000a00000001 ffff81003c4b8480
Aug 10 06:47:04 ubuntu kernel: [32950.771437]  ffff81003d45a600 ffff81003c4b8480 0000000000724910 000000000071ff50
Aug 10 06:47:04 ubuntu kernel: [32950.771447] Call Trace:
Aug 10 06:47:04 ubuntu kernel: [32950.771467]  [unionfs:unionfs_flush+0x1e/0x140] :unionfs:unionfs_flush+0x1e/0x140
Aug 10 06:47:04 ubuntu kernel: [32950.771482]  [filp_close+0x33/0x90] filp_close+0x33/0x90
Aug 10 06:47:04 ubuntu kernel: [32950.771492]  [sys_close+0x9f/0x100] sys_close+0x9f/0x100
Aug 10 06:47:04 ubuntu kernel: [32950.771502]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 10 06:47:04 ubuntu kernel: [32950.771513] 
Aug 10 06:47:04 ubuntu kernel: [32950.771519] 
Aug 10 06:47:04 ubuntu kernel: [32950.771519] Code: 48 8b 80 f8 00 00 00 f6 40 58 01 0f 84 8f fc ff ff 49 8b 56 
Aug 10 06:47:04 ubuntu kernel: [32950.771555] RIP  [unionfs:unionfs_file_revalidate+0x447/0x9b0] :unionfs:unionfs_file_revalidate+0x447/0x9b0
Aug 10 06:47:04 ubuntu kernel: [32950.771571]  RSP <ffff810022659e98>
Aug 10 06:47:04 ubuntu kernel: [32950.771577] CR2: 00000000000000f8
Aug 10 06:47:04 ubuntu kernel: [32950.771819] ---[ end trace 98a2f606d8cd9643 ]---
Aug 10 06:47:07 ubuntu syslogd 1.5.0#1ubuntu1: restart.

------------------------------------

Aug 17 06:47:05 ubuntu kernel: [25454.694275] PGD 1c4d5067 PUD 1c3cd067 PMD 0 
Aug 17 06:47:05 ubuntu kernel: [25454.694294] CPU 1 
Aug 17 06:47:05 ubuntu kernel: [25454.694301] Modules linked in: af_packet ext3 jbd mbcache ipv6 radeon drm rfcomm l2cap bluetooth ppdev lp powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video output sbs sbshc container dock ac iptable_filter ip_tables x_tables i2c_piix4 parport_pc i2c_core parport evdev button k8temp shpchp pci_hotplug pcspkr battery squashfs loop unionfs nls_cp437 isofs sg ide_cd cdrom sd_mod pata_atiixp pata_acpi ata_generic ahci libata atiixp r8169 scsi_mod ide_core thermal processor fan fbcon tileblit font bitblit softcursor fuse
Aug 17 06:47:05 ubuntu kernel: [25454.694425] Pid: 9763, comm: mandb Not tainted 2.6.24-19-generic #1
Aug 17 06:47:05 ubuntu kernel: [25454.694433] RIP: 0010:[unionfs:unionfs_file_revalidate+0x447/0x9b0]  [unionfs:unionfs_file_revalidate+0x447/0x9b0] :unionfs:unionfs_file_revalidate+0x447/0x9b0
Aug 17 06:47:05 ubuntu kernel: [25454.694450] RSP: 0018:ffff8100014d5e98  EFLAGS: 00010202
Aug 17 06:47:05 ubuntu kernel: [25454.694458] RAX: 0000000000000000 RBX: ffff81001a4edc00 RCX: 0000000000000000
Aug 17 06:47:05 ubuntu kernel: [25454.694964] RDX: ffff81001da2a600 RSI: 0000000000000000 RDI: ffff81001a4edc00
Aug 17 06:47:05 ubuntu kernel: [25454.694972] RBP: ffff81001c8c4000 R08: 0000000000000000 R09: ffff8100014d5dc8
Aug 17 06:47:05 ubuntu kernel: [25454.694980] R10: 0000000000000000 R11: 0000000000000246 R12: ffff81001c0af180
Aug 17 06:47:05 ubuntu kernel: [25454.694988] R13: 0000000000000001 R14: ffff81001c0af180 R15: ffff810000f71d00
Aug 17 06:47:05 ubuntu kernel: [25454.694996] FS:  00007fdba840e6e0(0000) GS:ffff81001d001700(0000) knlGS:0000000000000000
Aug 17 06:47:05 ubuntu kernel: [25454.695007] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 17 06:47:05 ubuntu kernel: [25454.695014] CR2: 00000000000000f8 CR3: 0000000000e8a000 CR4: 00000000000006e0
Aug 17 06:47:05 ubuntu kernel: [25454.695021] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 17 06:47:05 ubuntu kernel: [25454.695029] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 17 06:47:05 ubuntu kernel: [25454.695037] Process mandb (pid: 9763, threadinfo ffff8100014d4000, task ffff8100014b77a0)
Aug 17 06:47:05 ubuntu kernel: [25454.695048] Stack:  00000001014d5ec8 ffff81001db02c00 ffff8100014d5ee0 0000000000000001
Aug 17 06:47:05 ubuntu kernel: [25454.695065]  0000000000000008 01ff81001b282000 0000000a00000001 ffff81001c0af180
Aug 17 06:47:05 ubuntu kernel: [25454.695080]  ffff81001c8c4000 ffff81001c0af180 0000000000724910 000000000071ff50
Aug 17 06:47:05 ubuntu kernel: [25454.695091] Call Trace:
Aug 17 06:47:05 ubuntu kernel: [25454.695111]  [unionfs:unionfs_flush+0x1e/0x140] :unionfs:unionfs_flush+0x1e/0x140
Aug 17 06:47:05 ubuntu kernel: [25454.695126]  [filp_close+0x33/0x90] filp_close+0x33/0x90
Aug 17 06:47:05 ubuntu kernel: [25454.695136]  [sys_close+0x9f/0x100] sys_close+0x9f/0x100
Aug 17 06:47:05 ubuntu kernel: [25454.695145]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug 17 06:47:05 ubuntu kernel: [25454.695156] 
Aug 17 06:47:05 ubuntu kernel: [25454.695162] 
Aug 17 06:47:05 ubuntu kernel: [25454.695162] Code: 48 8b 80 f8 00 00 00 f6 40 58 01 0f 84 8f fc ff ff 49 8b 56 
Aug 17 06:47:05 ubuntu kernel: [25454.695213]  RSP <ffff8100014d5e98>
Aug 17 06:47:05 ubuntu kernel: [25454.695461] ---[ end trace 5216d24adc861d42 ]---

------------------------------------

Has anyone got any ideas what they could be for?

I have done an fsck on the drive a couple of weeks ago (no errors)... but might try again later just to be sure that is still the case.

---

