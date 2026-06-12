---
title: "LSI Megaraid 9240-8i on 12.04 LTS boot problem"
date: 2013-01-07
forum: Hardware
---

### Post by Zfs on 2013-01-07
I installed this card on a simple motherboard on the same ubuntu and it ran without problems. However, ever since I installed it on a Asrock X79 Extreme 11, I have this problem:

The system seems to freeze at boot time, but it continues booting after about 20 seconds.  The 8 x sata disks connected to the Megasas card don't show up in /dev/disk/by-id until 190 seconds after boot. After they appear, we can mount our 8x3TB zfs volume and all works perfectly from that point onwards.

I installed the newest version of the megasas dirver: v06.504.01.00-2_Ubuntu12.04.amd64.deb - and this still has the same problem.

Any ideas?

This is syslog|grep megasas:

```
Jan  7 12:11:41 galaxy kernel: [    1.871579] megasas: 00.00.06.12-rc1 Wed. Oct. 5 17:00:00 PDT 2011
Jan  7 12:11:41 galaxy kernel: [    1.871599] megasas: 0x1000:0x0073:0x1000:0x9240: bus 9:slot 0:func 0
Jan  7 12:11:41 galaxy kernel: [    1.871612] megaraid_sas 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  7 12:11:41 galaxy kernel: [    1.871616] megaraid_sas 0000:09:00.0: setting latency timer to 64
Jan  7 12:11:41 galaxy kernel: [    1.871671] megasas: FW now in Ready state
Jan  7 12:11:41 galaxy kernel: [    1.871712] megaraid_sas 0000:09:00.0: irq 92 for MSI/MSI-X
Jan  7 12:11:41 galaxy kernel: [    1.892086] megasas_init_mfi: fw_support_ieee=67108864
Jan  7 12:11:41 galaxy kernel: [    1.892091] megasas: INIT adapter done
Jan  7 12:13:42 galaxy kernel: [  190.816090] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 12:13:42 galaxy kernel: [  190.816096] megasas: [ 0]waiting for 1 commands to complete
Jan  7 12:13:47 galaxy kernel: [  195.836076] megasas: [ 5]waiting for 1 commands to complete
Jan  7 12:13:52 galaxy kernel: [  200.856075] megasas: [10]waiting for 1 commands to complete
Jan  7 12:13:57 galaxy kernel: [  205.876075] megasas: [15]waiting for 1 commands to complete
Jan  7 12:14:02 galaxy kernel: [  210.896041] megasas: [20]waiting for 1 commands to complete
Jan  7 12:14:07 galaxy kernel: [  215.916075] megasas: [25]waiting for 1 commands to complete
Jan  7 12:14:12 galaxy kernel: [  220.936078] megasas: [30]waiting for 1 commands to complete
Jan  7 12:14:17 galaxy kernel: [  225.956074] megasas: [35]waiting for 1 commands to complete
Jan  7 12:14:22 galaxy kernel: [  230.976078] megasas: [40]waiting for 1 commands to complete
Jan  7 12:14:27 galaxy kernel: [  235.996038] megasas: [45]waiting for 1 commands to complete
Jan  7 12:14:32 galaxy kernel: [  240.960193]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:14:32 galaxy kernel: [  240.960210]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:14:32 galaxy kernel: [  240.960220]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:14:32 galaxy kernel: [  240.960231]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:14:32 galaxy kernel: [  240.960342]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:14:32 galaxy kernel: [  241.016078] megasas: [50]waiting for 1 commands to complete
Jan  7 12:14:37 galaxy kernel: [  246.036077] megasas: [55]waiting for 1 commands to complete
Jan  7 12:14:42 galaxy kernel: [  251.056078] megasas: [60]waiting for 1 commands to complete
Jan  7 12:14:47 galaxy kernel: [  256.076078] megasas: [65]waiting for 1 commands to complete
Jan  7 12:14:52 galaxy kernel: [  261.096047] megasas: [70]waiting for 1 commands to complete
Jan  7 12:14:57 galaxy kernel: [  266.116077] megasas: [75]waiting for 1 commands to complete
Jan  7 12:15:02 galaxy kernel: [  271.136078] megasas: [80]waiting for 1 commands to complete
Jan  7 12:15:07 galaxy kernel: [  276.156078] megasas: [85]waiting for 1 commands to complete
Jan  7 12:15:12 galaxy kernel: [  281.176081] megasas: [90]waiting for 1 commands to complete
Jan  7 12:15:17 galaxy kernel: [  286.196070] megasas: [95]waiting for 1 commands to complete
Jan  7 12:15:22 galaxy kernel: [  291.216081] megasas: [100]waiting for 1 commands to complete
Jan  7 12:15:27 galaxy kernel: [  296.236078] megasas: [105]waiting for 1 commands to complete
Jan  7 12:15:32 galaxy kernel: [  301.256079] megasas: [110]waiting for 1 commands to complete
Jan  7 12:15:37 galaxy kernel: [  306.276074] megasas: [115]waiting for 1 commands to complete
Jan  7 12:15:42 galaxy kernel: [  311.296073] megasas: [120]waiting for 1 commands to complete
Jan  7 12:15:47 galaxy kernel: [  316.316075] megasas: [125]waiting for 1 commands to complete
Jan  7 12:15:52 galaxy kernel: [  321.336080] megasas: [130]waiting for 1 commands to complete
Jan  7 12:15:57 galaxy kernel: [  326.356072] megasas: [135]waiting for 1 commands to complete
Jan  7 12:16:03 galaxy kernel: [  331.376075] megasas: [140]waiting for 1 commands to complete
Jan  7 12:16:08 galaxy kernel: [  336.396073] megasas: [145]waiting for 1 commands to complete
Jan  7 12:16:13 galaxy kernel: [  341.416074] megasas: [150]waiting for 1 commands to complete
Jan  7 12:16:18 galaxy kernel: [  346.436071] megasas: [155]waiting for 1 commands to complete
Jan  7 12:16:23 galaxy kernel: [  351.456077] megasas: [160]waiting for 1 commands to complete
Jan  7 12:16:28 galaxy kernel: [  356.476077] megasas: [165]waiting for 1 commands to complete
Jan  7 12:16:32 galaxy kernel: [  360.961010]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:16:32 galaxy kernel: [  360.961027]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:16:32 galaxy kernel: [  360.961037]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:16:32 galaxy kernel: [  360.961048]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:16:32 galaxy kernel: [  360.961158]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:16:33 galaxy kernel: [  361.496075] megasas: [170]waiting for 1 commands to complete
Jan  7 12:16:38 galaxy kernel: [  366.516079] megasas: [175]waiting for 1 commands to complete
Jan  7 12:16:43 galaxy kernel: [  371.536080] megasas: moving cmd[0]:ffff88080757cb40:0:ffff880806d67900 the defer queue as internal
Jan  7 12:16:43 galaxy kernel: [  371.536086] megaraid_sas: FW detected to be in faultstate, restarting it...
Jan  7 12:16:54 galaxy kernel: [  382.544078] megaraid_sas: FW restarted successfully,initiating next stage...
Jan  7 12:16:54 galaxy kernel: [  382.544083] megaraid_sas: HBA recovery state machine,state 2 starting...
Jan  7 12:17:24 galaxy kernel: [  412.664080] megasas: Waiting for FW to come to ready state
Jan  7 12:17:24 galaxy kernel: [  412.680080] megasas: FW now in Ready state
Jan  7 12:17:24 galaxy kernel: [  412.752082] megaraid_sas: command ffff88080757cb40, ffff880806d67900:0detected to be pending while HBA reset.
Jan  7 12:17:24 galaxy kernel: [  412.752089] megasas: ffff88080757cb40 scsi cmd [12]detected on the internal queue, issue again.
Jan  7 12:17:25 galaxy kernel: [  413.756036] megasas: reset successful 
Jan  7 12:17:25 galaxy kernel: [  413.756097] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 12:17:25 galaxy kernel: [  413.756105] megaraid_sas: no pending cmds after reset
Jan  7 12:17:25 galaxy kernel: [  413.756108] megasas: reset successful 
Jan  7 12:17:35 galaxy kernel: [  423.760102] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 12:17:35 galaxy kernel: [  423.760110] megaraid_sas: no pending cmds after reset
Jan  7 12:17:35 galaxy kernel: [  423.760112] megasas: reset successful 
Jan  7 12:18:32 galaxy kernel: [  480.960178]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:18:32 galaxy kernel: [  480.960195]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:18:32 galaxy kernel: [  480.960204]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:18:32 galaxy kernel: [  480.960215]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:18:32 galaxy kernel: [  480.960326]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:20:32 galaxy kernel: [  600.960182]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:20:32 galaxy kernel: [  600.960199]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:20:32 galaxy kernel: [  600.960209]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:20:32 galaxy kernel: [  600.960219]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:20:32 galaxy kernel: [  600.960329]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:22:32 galaxy kernel: [  720.960186]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:22:32 galaxy kernel: [  720.960203]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:22:32 galaxy kernel: [  720.960212]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:22:32 galaxy kernel: [  720.960223]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:22:32 galaxy kernel: [  720.960333]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:24:32 galaxy kernel: [  840.960187]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:24:32 galaxy kernel: [  840.960204]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:24:32 galaxy kernel: [  840.960213]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:24:32 galaxy kernel: [  840.960224]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:24:32 galaxy kernel: [  840.960333]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:26:32 galaxy kernel: [  960.960182]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:26:32 galaxy kernel: [  960.960199]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:26:32 galaxy kernel: [  960.960208]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:26:32 galaxy kernel: [  960.960219]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:26:32 galaxy kernel: [  960.960329]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:28:32 galaxy kernel: [ 1080.960187]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:28:32 galaxy kernel: [ 1080.960204]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:28:32 galaxy kernel: [ 1080.960213]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:28:32 galaxy kernel: [ 1080.960224]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:28:32 galaxy kernel: [ 1080.960335]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:30:32 galaxy kernel: [ 1200.960187]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:30:32 galaxy kernel: [ 1200.960204]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:30:32 galaxy kernel: [ 1200.960214]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:30:32 galaxy kernel: [ 1200.960225]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:30:32 galaxy kernel: [ 1200.960335]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:32:32 galaxy kernel: [ 1320.960194]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:32:32 galaxy kernel: [ 1320.960211]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:32:32 galaxy kernel: [ 1320.960221]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:32:32 galaxy kernel: [ 1320.960231]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:32:32 galaxy kernel: [ 1320.960342]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:52:16 galaxy kernel: [    1.819362] megasas: 00.00.06.12-rc1 Wed. Oct. 5 17:00:00 PDT 2011
Jan  7 12:52:16 galaxy kernel: [    1.819386] megasas: 0x1000:0x0073:0x1000:0x9240: bus 9:slot 0:func 0
Jan  7 12:52:16 galaxy kernel: [    1.819401] megaraid_sas 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  7 12:52:16 galaxy kernel: [    1.819408] megaraid_sas 0000:09:00.0: setting latency timer to 64
Jan  7 12:52:16 galaxy kernel: [    1.819462] megasas: FW now in Ready state
Jan  7 12:52:16 galaxy kernel: [    1.819511] megaraid_sas 0000:09:00.0: irq 92 for MSI/MSI-X
Jan  7 12:52:16 galaxy kernel: [    1.840066] megasas_init_mfi: fw_support_ieee=67108864
Jan  7 12:52:16 galaxy kernel: [    1.840070] megasas: INIT adapter done
Jan  7 12:54:22 galaxy kernel: [  190.816087] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 12:54:22 galaxy kernel: [  190.816094] megasas: [ 0]waiting for 1 commands to complete
Jan  7 12:54:27 galaxy kernel: [  195.836079] megasas: [ 5]waiting for 1 commands to complete
Jan  7 12:54:32 galaxy kernel: [  200.856077] megasas: [10]waiting for 1 commands to complete
Jan  7 12:54:37 galaxy kernel: [  205.876077] megasas: [15]waiting for 1 commands to complete
Jan  7 12:54:42 galaxy kernel: [  210.896077] megasas: [20]waiting for 1 commands to complete
Jan  7 12:54:47 galaxy kernel: [  215.916075] megasas: [25]waiting for 1 commands to complete
Jan  7 12:54:52 galaxy kernel: [  220.936073] megasas: [30]waiting for 1 commands to complete
Jan  7 12:54:57 galaxy kernel: [  225.956074] megasas: [35]waiting for 1 commands to complete
Jan  7 12:55:02 galaxy kernel: [  230.976078] megasas: [40]waiting for 1 commands to complete
Jan  7 12:55:07 galaxy kernel: [  235.996081] megasas: [45]waiting for 1 commands to complete
Jan  7 12:55:12 galaxy kernel: [  240.960186]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:55:12 galaxy kernel: [  240.960203]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:55:12 galaxy kernel: [  240.960212]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:55:12 galaxy kernel: [  240.960223]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:55:12 galaxy kernel: [  240.960331]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:55:12 galaxy kernel: [  241.016078] megasas: [50]waiting for 1 commands to complete
Jan  7 12:55:17 galaxy kernel: [  246.036076] megasas: [55]waiting for 1 commands to complete
Jan  7 12:55:22 galaxy kernel: [  251.056075] megasas: [60]waiting for 1 commands to complete
Jan  7 12:55:27 galaxy kernel: [  256.076080] megasas: [65]waiting for 1 commands to complete
Jan  7 12:55:32 galaxy kernel: [  261.096078] megasas: [70]waiting for 1 commands to complete
Jan  7 12:55:37 galaxy kernel: [  266.116078] megasas: [75]waiting for 1 commands to complete
Jan  7 12:55:42 galaxy kernel: [  271.136077] megasas: [80]waiting for 1 commands to complete
Jan  7 12:55:47 galaxy kernel: [  276.156074] megasas: [85]waiting for 1 commands to complete
Jan  7 12:55:52 galaxy kernel: [  281.176077] megasas: [90]waiting for 1 commands to complete
Jan  7 12:55:57 galaxy kernel: [  286.196076] megasas: [95]waiting for 1 commands to complete
Jan  7 12:56:02 galaxy kernel: [  291.216075] megasas: [100]waiting for 1 commands to complete
Jan  7 12:56:08 galaxy kernel: [  296.236076] megasas: [105]waiting for 1 commands to complete
Jan  7 12:56:13 galaxy kernel: [  301.256073] megasas: [110]waiting for 1 commands to complete
Jan  7 12:56:18 galaxy kernel: [  306.276074] megasas: [115]waiting for 1 commands to complete
Jan  7 12:56:23 galaxy kernel: [  311.296075] megasas: [120]waiting for 1 commands to complete
Jan  7 12:56:28 galaxy kernel: [  316.316077] megasas: [125]waiting for 1 commands to complete
Jan  7 12:56:33 galaxy kernel: [  321.336077] megasas: [130]waiting for 1 commands to complete
Jan  7 12:56:38 galaxy kernel: [  326.356079] megasas: [135]waiting for 1 commands to complete
Jan  7 12:56:43 galaxy kernel: [  331.376078] megasas: [140]waiting for 1 commands to complete
Jan  7 12:56:48 galaxy kernel: [  336.396080] megasas: [145]waiting for 1 commands to complete
Jan  7 12:56:53 galaxy kernel: [  341.416076] megasas: [150]waiting for 1 commands to complete
Jan  7 12:56:58 galaxy kernel: [  346.436075] megasas: [155]waiting for 1 commands to complete
Jan  7 12:57:03 galaxy kernel: [  351.456080] megasas: [160]waiting for 1 commands to complete
Jan  7 12:57:08 galaxy kernel: [  356.476082] megasas: [165]waiting for 1 commands to complete
Jan  7 12:57:12 galaxy kernel: [  360.960190]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:57:12 galaxy kernel: [  360.960207]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:57:12 galaxy kernel: [  360.960217]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:57:12 galaxy kernel: [  360.960227]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:57:12 galaxy kernel: [  360.960336]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 12:57:13 galaxy kernel: [  361.496077] megasas: [170]waiting for 1 commands to complete
Jan  7 12:57:18 galaxy kernel: [  366.516075] megasas: [175]waiting for 1 commands to complete
Jan  7 12:57:23 galaxy kernel: [  371.536080] megasas: moving cmd[0]:ffff880807054720:0:ffff8808064b3300 the defer queue as internal
Jan  7 12:57:23 galaxy kernel: [  371.536086] megaraid_sas: FW detected to be in faultstate, restarting it...
Jan  7 12:57:34 galaxy kernel: [  382.544072] megaraid_sas: FW restarted successfully,initiating next stage...
Jan  7 12:57:34 galaxy kernel: [  382.544078] megaraid_sas: HBA recovery state machine,state 2 starting...
Jan  7 12:58:04 galaxy kernel: [  412.664073] megasas: Waiting for FW to come to ready state
Jan  7 12:58:04 galaxy kernel: [  412.680077] megasas: FW now in Ready state
Jan  7 12:58:04 galaxy kernel: [  412.752079] megaraid_sas: command ffff880807054720, ffff8808064b3300:0detected to be pending while HBA reset.
Jan  7 12:58:04 galaxy kernel: [  412.752086] megasas: ffff880807054720 scsi cmd [12]detected on the internal queue, issue again.
Jan  7 12:58:05 galaxy kernel: [  413.756076] megasas: reset successful 
Jan  7 12:58:05 galaxy kernel: [  413.756148] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 12:58:05 galaxy kernel: [  413.756155] megaraid_sas: no pending cmds after reset
Jan  7 12:58:05 galaxy kernel: [  413.756158] megasas: reset successful 
Jan  7 12:58:15 galaxy kernel: [  423.760160] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 12:58:15 galaxy kernel: [  423.760168] megaraid_sas: no pending cmds after reset
Jan  7 12:58:15 galaxy kernel: [  423.760171] megasas: reset successful 
Jan  7 12:59:12 galaxy kernel: [  480.960190]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 12:59:12 galaxy kernel: [  480.960207]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 12:59:12 galaxy kernel: [  480.960216]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 12:59:12 galaxy kernel: [  480.960227]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 12:59:12 galaxy kernel: [  480.960335]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:01:12 galaxy kernel: [  600.960183]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:01:12 galaxy kernel: [  600.960199]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:01:12 galaxy kernel: [  600.960209]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:01:12 galaxy kernel: [  600.960219]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:01:12 galaxy kernel: [  600.960328]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:03:12 galaxy kernel: [  720.960191]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:03:12 galaxy kernel: [  720.960208]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:03:12 galaxy kernel: [  720.960218]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:03:12 galaxy kernel: [  720.960229]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:03:12 galaxy kernel: [  720.960338]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:05:12 galaxy kernel: [  840.960186]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:05:12 galaxy kernel: [  840.960203]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:05:12 galaxy kernel: [  840.960213]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:05:12 galaxy kernel: [  840.960223]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:05:12 galaxy kernel: [  840.960332]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:07:12 galaxy kernel: [  960.961187]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:07:12 galaxy kernel: [  960.961204]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:07:12 galaxy kernel: [  960.961213]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:07:12 galaxy kernel: [  960.961224]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:07:12 galaxy kernel: [  960.961333]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:09:12 galaxy kernel: [ 1080.961380]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:09:12 galaxy kernel: [ 1080.961397]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:09:12 galaxy kernel: [ 1080.961406]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:09:12 galaxy kernel: [ 1080.961417]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:09:12 galaxy kernel: [ 1080.961526]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:11:12 galaxy kernel: [ 1200.961469]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:11:12 galaxy kernel: [ 1200.961487]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:11:12 galaxy kernel: [ 1200.961496]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:11:12 galaxy kernel: [ 1200.961507]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:11:12 galaxy kernel: [ 1200.961615]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 13:13:12 galaxy kernel: [ 1320.961206]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 13:13:12 galaxy kernel: [ 1320.961224]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 13:13:12 galaxy kernel: [ 1320.961233]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 13:13:12 galaxy kernel: [ 1320.961244]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 13:13:12 galaxy kernel: [ 1320.961353]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 14:47:43 galaxy kernel: [    1.852092] megasas: 00.00.06.12-rc1 Wed. Oct. 5 17:00:00 PDT 2011
Jan  7 14:47:43 galaxy kernel: [    1.852116] megasas: 0x1000:0x0073:0x1000:0x9240: bus 9:slot 0:func 0
Jan  7 14:47:43 galaxy kernel: [    1.852131] megaraid_sas 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  7 14:47:43 galaxy kernel: [    1.852138] megaraid_sas 0000:09:00.0: setting latency timer to 64
Jan  7 14:47:43 galaxy kernel: [    1.852315] megasas: FW now in Ready state
Jan  7 14:47:43 galaxy kernel: [    1.852363] megaraid_sas 0000:09:00.0: irq 92 for MSI/MSI-X
Jan  7 14:47:43 galaxy kernel: [    1.880098] megasas_init_mfi: fw_support_ieee=67108864
Jan  7 14:47:43 galaxy kernel: [    1.880102] megasas: INIT adapter done
Jan  7 14:49:49 galaxy kernel: [  190.816084] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 14:49:49 galaxy kernel: [  190.816090] megasas: [ 0]waiting for 1 commands to complete
Jan  7 14:49:54 galaxy kernel: [  195.836076] megasas: [ 5]waiting for 1 commands to complete
Jan  7 14:49:59 galaxy kernel: [  200.856081] megasas: [10]waiting for 1 commands to complete
Jan  7 14:50:04 galaxy kernel: [  205.876080] megasas: [15]waiting for 1 commands to complete
Jan  7 14:50:09 galaxy kernel: [  210.896078] megasas: [20]waiting for 1 commands to complete
Jan  7 14:50:14 galaxy kernel: [  215.916076] megasas: [25]waiting for 1 commands to complete
Jan  7 14:50:19 galaxy kernel: [  220.936047] megasas: [30]waiting for 1 commands to complete
Jan  7 14:50:24 galaxy kernel: [  225.956082] megasas: [35]waiting for 1 commands to complete
Jan  7 14:50:29 galaxy kernel: [  230.976078] megasas: [40]waiting for 1 commands to complete
Jan  7 14:50:34 galaxy kernel: [  235.996080] megasas: [45]waiting for 1 commands to complete
Jan  7 14:50:39 galaxy kernel: [  240.966317]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 14:50:39 galaxy kernel: [  240.966333]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 14:50:39 galaxy kernel: [  240.966343]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 14:50:39 galaxy kernel: [  240.966353]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 14:50:39 galaxy kernel: [  240.966462]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 14:50:39 galaxy kernel: [  241.016077] megasas: [50]waiting for 1 commands to complete
Jan  7 14:50:44 galaxy kernel: [  246.036075] megasas: [55]waiting for 1 commands to complete
Jan  7 14:50:49 galaxy kernel: [  251.056084] megasas: [60]waiting for 1 commands to complete
Jan  7 14:50:54 galaxy kernel: [  256.076077] megasas: [65]waiting for 1 commands to complete
Jan  7 14:50:59 galaxy kernel: [  261.096073] megasas: [70]waiting for 1 commands to complete
Jan  7 14:51:04 galaxy kernel: [  266.116075] megasas: [75]waiting for 1 commands to complete
Jan  7 14:51:09 galaxy kernel: [  271.136076] megasas: [80]waiting for 1 commands to complete
Jan  7 14:51:14 galaxy kernel: [  276.156079] megasas: [85]waiting for 1 commands to complete
Jan  7 14:51:20 galaxy kernel: [  281.176076] megasas: [90]waiting for 1 commands to complete
Jan  7 14:51:25 galaxy kernel: [  286.196080] megasas: [95]waiting for 1 commands to complete
Jan  7 14:51:30 galaxy kernel: [  291.216076] megasas: [100]waiting for 1 commands to complete
Jan  7 14:51:35 galaxy kernel: [  296.236081] megasas: [105]waiting for 1 commands to complete
Jan  7 14:51:40 galaxy kernel: [  301.256076] megasas: [110]waiting for 1 commands to complete
Jan  7 14:51:45 galaxy kernel: [  306.276078] megasas: [115]waiting for 1 commands to complete
Jan  7 14:51:50 galaxy kernel: [  311.296078] megasas: [120]waiting for 1 commands to complete
Jan  7 14:51:55 galaxy kernel: [  316.316078] megasas: [125]waiting for 1 commands to complete
Jan  7 14:52:00 galaxy kernel: [  321.336078] megasas: [130]waiting for 1 commands to complete
Jan  7 14:52:05 galaxy kernel: [  326.356083] megasas: [135]waiting for 1 commands to complete
Jan  7 14:52:10 galaxy kernel: [  331.376075] megasas: [140]waiting for 1 commands to complete
Jan  7 14:52:15 galaxy kernel: [  336.396075] megasas: [145]waiting for 1 commands to complete
Jan  7 14:52:20 galaxy kernel: [  341.416076] megasas: [150]waiting for 1 commands to complete
Jan  7 14:52:25 galaxy kernel: [  346.436072] megasas: [155]waiting for 1 commands to complete
Jan  7 14:52:30 galaxy kernel: [  351.456074] megasas: [160]waiting for 1 commands to complete
Jan  7 14:52:35 galaxy kernel: [  356.476071] megasas: [165]waiting for 1 commands to complete
Jan  7 14:52:39 galaxy kernel: [  360.970077]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 14:52:39 galaxy kernel: [  360.970092]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 14:52:39 galaxy kernel: [  360.970102]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 14:52:39 galaxy kernel: [  360.970113]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 14:52:39 galaxy kernel: [  360.970222]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 14:52:40 galaxy kernel: [  361.496075] megasas: [170]waiting for 1 commands to complete
Jan  7 14:52:45 galaxy kernel: [  366.516081] megasas: [175]waiting for 1 commands to complete
Jan  7 14:52:50 galaxy kernel: [  371.536027] megasas: moving cmd[0]:ffff88080895db40:0:ffff880806403100 the defer queue as internal
Jan  7 14:52:50 galaxy kernel: [  371.536032] megaraid_sas: FW detected to be in faultstate, restarting it...
Jan  7 14:53:01 galaxy kernel: [  382.544077] megaraid_sas: FW restarted successfully,initiating next stage...
Jan  7 14:53:01 galaxy kernel: [  382.544083] megaraid_sas: HBA recovery state machine,state 2 starting...
Jan  7 14:53:31 galaxy kernel: [  412.664081] megasas: Waiting for FW to come to ready state
Jan  7 14:53:31 galaxy kernel: [  412.680075] megasas: FW now in Ready state
Jan  7 14:53:31 galaxy kernel: [  412.752081] megaraid_sas: command ffff88080895db40, ffff880806403100:0detected to be pending while HBA reset.
Jan  7 14:53:31 galaxy kernel: [  412.752088] megasas: ffff88080895db40 scsi cmd [12]detected on the internal queue, issue again.
Jan  7 14:53:32 galaxy kernel: [  413.756079] megasas: reset successful 
Jan  7 14:53:32 galaxy kernel: [  413.756163] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 14:53:32 galaxy kernel: [  413.756171] megaraid_sas: no pending cmds after reset
Jan  7 14:53:32 galaxy kernel: [  413.756174] megasas: reset successful 
Jan  7 14:53:42 galaxy kernel: [  423.760072] scsi 8:0:0:0: megasas: RESET cmd=12 retries=0
Jan  7 14:53:42 galaxy kernel: [  423.760080] megaraid_sas: no pending cmds after reset
Jan  7 14:53:42 galaxy kernel: [  423.760083] megasas: reset successful 
Jan  7 14:54:39 galaxy kernel: [  480.969510]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 14:54:39 galaxy kernel: [  480.969528]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 14:54:39 galaxy kernel: [  480.969537]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 14:54:39 galaxy kernel: [  480.969548]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 14:54:39 galaxy kernel: [  480.969660]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]
Jan  7 14:56:39 galaxy kernel: [  600.969550]  [<ffffffffa00013f5>] megasas_issue_blocked_cmd+0x75/0xb0 [megaraid_sas]
Jan  7 14:56:39 galaxy kernel: [  600.969567]  [<ffffffffa00026c9>] megasas_get_seq_num+0xd9/0x260 [megaraid_sas]
Jan  7 14:56:39 galaxy kernel: [  600.969577]  [<ffffffffa0002b31>] megasas_start_aen+0x31/0x60 [megaraid_sas]
Jan  7 14:56:39 galaxy kernel: [  600.969588]  [<ffffffffa000b6f1>] megasas_probe_one+0x69a/0x81c [megaraid_sas]
Jan  7 14:56:39 galaxy kernel: [  600.969699]  [<ffffffffa001609e>] megasas_init+0x9e/0x1000 [megaraid_sas]

```

---

### Post by tgalati4 on 2013-01-07
Look for switches in the BIOS (motherboard BIOS, not RAID BIOS).  There may be an auto detection routine looking for local SATA drives which messes up booting of the LSI RAID controller.

---

### Post by Zfs on 2013-01-08
I went into the motherboard Bios;

- updated the bios to V2.20
- looked at all the onboard storage options
- disabled all the "bootable" options on the onboard sata controller, as well as the on-board LSI controller
- enabled only the minimum sata controllers for the 18 disks (2 x 8disk arrays, one hot spare and one SSD boot disk)

The problem persists.  Boot seems to freeze up - caused by one command the the megasas driver that hangs.

---

### Post by Paradoxalley on 2013-01-31
Looks like you are having some problems with driver conflict. can you post the output of the following:

lsmod
modinfo megaraid_sas
dmesg (full output, don't grep for megasas)
lspci -v

from looking at the specs for your board, it seems the onboard sas/sata controller is also an LSI chipset (SAS2308) and you are likely going to have to blacklist all other LSI modules for it in order to have only the 9240 driver load.

disabling the onboard RAID in BIOS is certainly a step in the right direction. BTW, is there a reason you are not using the included megaraid_sas driver?

---

