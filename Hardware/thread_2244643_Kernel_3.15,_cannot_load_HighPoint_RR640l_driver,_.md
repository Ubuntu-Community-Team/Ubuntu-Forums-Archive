---
title: "Kernel 3.15, cannot load HighPoint RR640l driver, Ubuntu 14.04"
date: 2014-09-17
forum: Hardware
---

### Post by evansed on 2014-09-17
[SIZE=3][FONT=times new roman]We installed a HighPoint Rocket Raid rr640l card.  It keeps disabling the SansDigital [/FONT]**TowerRAID TR8M6G **[FONT=times new roman] after several resets.  [/FONT][/SIZE]

Sep 17 15:00:00 biobionode1 kernel: [  864.920276] rr640l:[0 2  ] start port.
Sep 17 15:00:00 biobionode1 kernel: [  864.920281] rr640l:[0 2  ] start port hard reset (probe 1).
Sep 17 15:00:00 biobionode1 kernel: [  865.118734] rr640l:[0 3  ] start port.
Sep 17 15:00:00 biobionode1 kernel: [  865.118736] rr640l:[0 3  ] start port hard reset (probe 1).
Sep 17 15:00:03 biobionode1 kernel: [  867.383644] rr640l:[0 0 0] start device soft reset.
Sep 17 15:00:03 biobionode1 kernel: [  868.043731] rr640l:[0 1  ] port started successfully.
Sep 17 15:00:04 biobionode1 kernel: [  868.153779] rr640l:[0 0 0] config_device path_id :0 
Sep 17 15:00:04 biobionode1 kernel: [  868.154779] rr640l:[0 0 1] start device soft reset.
Sep 17 15:00:04 biobionode1 kernel: [  868.909901] rr640l:[0 0 1] config_device path_id :0 
Sep 17 15:00:04 biobionode1 kernel: [  868.922839] rr640l:[0 0  ] port started successfully.
Sep 17 15:00:04 biobionode1 kernel: [  868.922841] rr640l:[0 0 0] device probed successfully.
Sep 17 15:00:04 biobionode1 kernel: [  868.945438] rr640l:Backup stamp 5261775f sum 0 backed 1
Sep 17 15:00:04 biobionode1 kernel: [  868.953392] rr640l:Master stamp 5261775f sum 0 backed 1
Sep 17 15:00:04 biobionode1 kernel: [  868.953395] rr640l:raw ffff88085028f038 bad_sector 0
Sep 17 15:00:04 biobionode1 kernel: [  868.959363] rr640l:[0 0 1] device probed successfully.
Sep 17 15:00:04 biobionode1 kernel: [  868.982953] rr640l:Backup stamp 5261775f sum 0 backed 1
Sep 17 15:00:04 biobionode1 kernel: [  868.987926] rr640l:Master stamp 5261775f sum 0 backed 1
Sep 17 15:00:04 biobionode1 kernel: [  868.987928] rr640l:raw ffff88085028f838 bad_sector 0
Sep 17 15:00:04 biobionode1 kernel: [  869.090985] rr640l:[0 2  ] failed to hard reset.
Sep 17 15:00:04 biobionode1 kernel: [  869.090993] rr640l:[0 2  ] failed to perform port hard reset.
Sep 17 15:00:04 biobionode1 kernel: [  869.295010] rr640l:[0 3  ] failed to hard reset. [SIZE=2][COLOR=#393939]Sep 17 15:00:04 biobionode1 kernel: [  869.295019] rr640l:[0 3  ] failed to perform port hard reset.[/COLOR] 
[/SIZE]Sep 17 15:01:14 biobionode1 kernel: [  938.162395] rr640l:[0 0  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.162400] rr640l:[0 0  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.163397] rr640l:[0 0  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.163399] rr640l:[0 0  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.191244] rr640l:[0 0  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.191246] rr640l:[0 0  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.192242] rr640l:[0 0  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.192244] rr640l:[0 0  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.193242] rr640l:[0 0  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.193246] rr640l:[0 0  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.194243] rr640l:[0 0  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.194245] rr640l:[0 0  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.732840] rr640l:[0 1  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.732846] rr640l:[0 1  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.733842] rr640l:[0 1  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.733844] rr640l:[0 1  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.828250] rr640l:[0 1  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.828252] rr640l:[0 1  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.829249] rr640l:[0 1  ] port handle error (irq status 08000000)
Sep 17 15:01:14 biobionode1 kernel: [  938.829251] rr640l:[0 1  ] target interface fatal error
Sep 17 15:01:14 biobionode1 kernel: [  938.841380] scsi 13:0:0:0: Direct-Access     HPT      DISK_13_0        4.00 PQ: 0 ANSI: 5
Sep 17 15:01:14 biobionode1 kernel: [  938.841617] sd 13:0:0:0: [sde] 41022521344 512-byte logical blocks: (21.0 TB/19.1 TiB)
Sep 17 15:01:14 biobionode1 kernel: [  938.841642] sd 13:0:0:0: [sde] Write Protect is off
Sep 17 15:01:14 biobionode1 kernel: [  938.841645] sd 13:0:0:0: [sde] Mode Sense: 2f 00 00 00
Sep 17 15:01:14 biobionode1 kernel: [  938.841657] sd 13:0:0:0: Attached scsi generic sg5 type 0
Sep 17 15:01:14 biobionode1 kernel: [  938.841661] sd 13:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 17 15:01:17 biobionode1 kernel: [  940.057593] rr640l:[0 0 0] start device soft reset.
Sep 17 15:01:17 biobionode1 kernel: [  940.705747] rr640l:[0 1 0] start device soft reset.
Sep 17 15:01:17 biobionode1 kernel: [  941.357894] rr640l:[0 0 0] config_device path_id :0 
Sep 17 15:01:17 biobionode1 kernel: [  941.368841] rr640l:[0 0  ] port started successfully.
Sep 17 15:01:17 biobionode1 kernel: [  941.368842] rr640l:[0 0 0] device done to reset (reset 1)
Sep 17 15:01:17 biobionode1 kernel: [  941.373820] rr640l:[0 1 0] config_device path_id :1 
Sep 17 15:01:17 biobionode1 kernel: [  941.374816] rr640l:[0 1 3] start device soft reset.
Sep 17 15:01:17 biobionode1 kernel: [  942.125966] rr640l:[0 1 3] config_device path_id :1 
Sep 17 15:01:17 biobionode1 kernel: [  942.136914] rr640l:[0 1  ] port started successfully.
Sep 17 15:01:17 biobionode1 kernel: [  942.136916] rr640l:[0 1 0] device done to reset (reset 5)
Sep 17 15:01:17 biobionode1 kernel: [  942.136918] rr640l:[0 1 3] device done to reset (reset 3)
Sep 17 15:01:36 biobionode1 kernel: [  960.925599] rr640l:[0 0 1] start device soft reset.
Sep 17 15:01:38 biobionode1 kernel: [  961.745745] rr640l:[0 1 3] start device soft reset.
Sep 17 15:01:38 biobionode1 kernel: [  962.397879] rr640l:[0 0 1] config_device path_id :0 
Sep 17 15:01:38 biobionode1 kernel: [  962.398876] rr640l:[0 0 2] start device soft reset.
Sep 17 15:01:38 biobionode1 kernel: [  963.051017] rr640l:[0 1 3] config_device path_id :1 
Sep 17 15:01:38 biobionode1 kernel: [  963.061966] rr640l:[0 1  ] port started successfully.
Sep 17 15:01:38 biobionode1 kernel: [  963.061968] rr640l:[0 1 3] device done to reset (reset 4)
Sep 17 15:01:39 biobionode1 kernel: [  963.145997] rr640l:[0 0 2] config_device path_id :0 
Sep 17 15:01:39 biobionode1 kernel: [  963.146996] rr640l:[0 0 3] start device soft reset.
Sep 17 15:01:39 biobionode1 kernel: [  963.893127] rr640l:[0 0 3] config_device path_id :0 
Sep 17 15:01:39 biobionode1 kernel: [  963.904080] rr640l:[0 0  ] port started successfully.
Sep 17 15:01:39 biobionode1 kernel: [  963.904083] rr640l:[0 0 1] device done to reset (reset 1)
Sep 17 15:01:39 biobionode1 kernel: [  963.904085] rr640l:[0 0 2] device done to reset (reset 5)
Sep 17 15:01:39 biobionode1 kernel: [  963.904087] rr640l:[0 0 3] device done to reset (reset 4)
Sep 17 15:01:44 biobionode1 kernel: [  969.178254] rr640l:hpt_reset(13/0/0)
Sep 17 15:01:46 biobionode1 kernel: [  970.815491] rr640l:[0 0 1] start device soft reset.
Sep 17 15:01:47 biobionode1 kernel: [  971.571632] rr640l:[0 1 3] start device soft reset.
Sep 17 15:01:47 biobionode1 kernel: [  972.223759] rr640l:[0 0 1] config_device path_id :0 
Sep 17 15:01:47 biobionode1 kernel: [  972.234706] rr640l:[0 0  ] port started successfully.
Sep 17 15:01:47 biobionode1 kernel: [  972.234707] rr640l:[0 0 1] device done to reset (reset 2)
Sep 17 15:01:47 biobionode1 kernel: [  972.323752] rr640l:[0 1 3] config_device path_id :1 
Sep 17 15:01:47 biobionode1 kernel: [  972.334701] rr640l:[0 1  ] port started successfully.
Sep 17 15:01:47 biobionode1 kernel: [  972.334703] rr640l:[0 1 3] device done to reset (reset 5)
Sep 17 15:01:47 biobionode1 kernel: [  972.590867] rr640l:[0 1 3] too many resets - make device offline.

[SIZE=3]We have tried irqpoll and compiled from scratch, but that did not help.  Does anyone have any suggestions?  Any help would be greatly appreciated.[/SIZE]

---

### Post by gale-michael on 2015-01-08
Hello,

    By any chance did you find a solution to this issue?

Michael

---

