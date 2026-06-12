---
title: "failed command: WRITE DMA"
date: 2011-01-27
forum: Hardware
---

### Post by TheNerdAL on 2011-01-27
When I boot up my computer, it takes a long time and has a "failed command: WRITE DMA" error with other lines that looks like the command line, can anyone help me?

I replaced the 40 conductor cable from my old Hard drive to a 80 conductor cable and it didn't fix it. :( 

Thanks.

---

### Post by coffee412 on 2011-01-27
> **TheNerdAL said:**
> When I boot up my computer, it takes a long time and has a "failed command: WRITE DMA" error with other lines that looks like the command line, can anyone help me?

I replaced the 40 conductor cable from my old Hard drive to a 80 conductor cable and it didn't fix it. :( 

Thanks.

One of your devices (cdrom/dvd/hard drive) failed to take a command for some reason. 

If you can get booted up with Ubuntu or from a install disk check your logs. Look for any block device errors (hard drive ect..) Perhaps you replaced a cable with another bad one? I would go back to the original cable unless you know for sure its toast.

when you get into a term window issue the command below:

sudo cat /var/log/messages |grep sd

It will show all lines with "sd" in them (i.e. /dev/sda). Check the lines and if something looks a miss then remember which device is reporting it. 

Perhaps you might have loosened a cable while inside the box. I would check them.

Post what you find if you can.

---

### Post by TheNerdAL on 2011-01-27
```
adrian@adrian-desktop:~$ sudo cat /var/log/messages |grep sd
[sudo] password for adrian: 
Jan 24 07:25:14 adrian-desktop kernel: [    1.785361] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 24 07:25:14 adrian-desktop kernel: [    1.785555] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 24 07:25:14 adrian-desktop kernel: [    1.785622] sd 0:0:0:0: [sda] Write Protect is off
Jan 24 07:25:14 adrian-desktop kernel: [    1.785652] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 24 07:25:14 adrian-desktop kernel: [    1.785856]  sda: sda1 sda2 <
Jan 24 07:25:14 adrian-desktop kernel: [    1.830046]  sda5 >
Jan 24 07:25:14 adrian-desktop kernel: [    1.830345] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 24 07:25:14 adrian-desktop kernel: [    4.143748] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 24 07:25:14 adrian-desktop kernel: [    4.143896] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 24 07:25:14 adrian-desktop kernel: [    4.144064] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 24 07:25:14 adrian-desktop kernel: [    4.144210] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 24 07:25:14 adrian-desktop kernel: [    4.191556] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 24 07:25:14 adrian-desktop kernel: [    4.366574] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 24 07:25:14 adrian-desktop kernel: [    4.377641] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 24 07:25:14 adrian-desktop kernel: [    4.388604] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 24 07:25:14 adrian-desktop kernel: [    4.410583] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 24 07:25:14 adrian-desktop kernel: [   12.945744] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 24 07:25:14 adrian-desktop kernel: [  178.117210] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 24 07:25:14 adrian-desktop kernel: [  178.567020] type=1400 audit(1295875514.275:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=898 comm="apparmor_parser"
Jan 24 07:25:20 adrian-desktop kernel: [  184.813934] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 24 16:29:54 adrian-desktop kernel: [    1.789001] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 24 16:29:54 adrian-desktop kernel: [    1.789191] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 24 16:29:54 adrian-desktop kernel: [    1.789257] sd 0:0:0:0: [sda] Write Protect is off
Jan 24 16:29:54 adrian-desktop kernel: [    1.789287] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 24 16:29:54 adrian-desktop kernel: [    1.789487]  sda:
Jan 24 16:29:54 adrian-desktop kernel: [    1.792169]  sda1 sda2 <
Jan 24 16:29:54 adrian-desktop kernel: [    1.828631]  sda5 >
Jan 24 16:29:54 adrian-desktop kernel: [    1.828936] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 24 16:29:54 adrian-desktop kernel: [    4.146200] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 24 16:29:54 adrian-desktop kernel: [    4.146346] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 24 16:29:54 adrian-desktop kernel: [    4.146489] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 24 16:29:54 adrian-desktop kernel: [    4.146629] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 24 16:29:54 adrian-desktop kernel: [    4.198556] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 24 16:29:54 adrian-desktop kernel: [    4.369808] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 24 16:29:54 adrian-desktop kernel: [    4.380675] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 24 16:29:54 adrian-desktop kernel: [    4.392086] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 24 16:29:54 adrian-desktop kernel: [    4.413691] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 24 16:29:54 adrian-desktop kernel: [   13.065282] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 24 16:29:54 adrian-desktop kernel: [  177.092800] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 24 16:29:54 adrian-desktop kernel: [  177.592357] type=1400 audit(1295908194.298:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=895 comm="apparmor_parser"
Jan 24 16:29:57 adrian-desktop kernel: [  180.569483] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 24 16:29:59 adrian-desktop kernel: [  182.535418] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 25 16:46:16 adrian-desktop kernel: [    1.789064] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 25 16:46:16 adrian-desktop kernel: [    1.789256] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 25 16:46:16 adrian-desktop kernel: [    1.789321] sd 0:0:0:0: [sda] Write Protect is off
Jan 25 16:46:16 adrian-desktop kernel: [    1.789351] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 25 16:46:16 adrian-desktop kernel: [    1.789545]  sda:
Jan 25 16:46:16 adrian-desktop kernel: [    1.795469]  sda1 sda2 <
Jan 25 16:46:16 adrian-desktop kernel: [    1.831933]  sda5 >
Jan 25 16:46:16 adrian-desktop kernel: [    1.832321] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 25 16:46:16 adrian-desktop kernel: [    4.143695] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 25 16:46:16 adrian-desktop kernel: [    4.143842] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 25 16:46:16 adrian-desktop kernel: [    4.143987] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 25 16:46:16 adrian-desktop kernel: [    4.144155] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 25 16:46:16 adrian-desktop kernel: [    4.202898] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 25 16:46:16 adrian-desktop kernel: [    4.366533] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 25 16:46:16 adrian-desktop kernel: [    4.377514] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 25 16:46:16 adrian-desktop kernel: [    4.388512] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 25 16:46:16 adrian-desktop kernel: [    4.411556] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 25 16:46:16 adrian-desktop kernel: [   13.218504] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 25 16:46:16 adrian-desktop kernel: [  178.116776] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 25 16:46:16 adrian-desktop kernel: [  178.655377] type=1400 audit(1295995576.360:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=906 comm="apparmor_parser"
Jan 25 16:46:26 adrian-desktop kernel: [  185.187768] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 25 21:50:34 adrian-desktop kernel: [    1.785104] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 25 21:50:34 adrian-desktop kernel: [    1.785299] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 25 21:50:34 adrian-desktop kernel: [    1.785365] sd 0:0:0:0: [sda] Write Protect is off
Jan 25 21:50:34 adrian-desktop kernel: [    1.785395] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 25 21:50:34 adrian-desktop kernel: [    1.785592]  sda:
Jan 25 21:50:34 adrian-desktop kernel: [    1.790206]  sda1 sda2 <
Jan 25 21:50:34 adrian-desktop kernel: [    1.818335]  sda5 >
Jan 25 21:50:34 adrian-desktop kernel: [    1.818643] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 25 21:50:34 adrian-desktop kernel: [    4.088137] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 25 21:50:34 adrian-desktop kernel: [    4.138088] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 25 21:50:34 adrian-desktop kernel: [    4.138233] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 25 21:50:34 adrian-desktop kernel: [    4.138375] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 25 21:50:34 adrian-desktop kernel: [    4.138514] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 25 21:50:34 adrian-desktop kernel: [    4.342569] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 25 21:50:34 adrian-desktop kernel: [    4.353562] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 25 21:50:34 adrian-desktop kernel: [    4.364557] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 25 21:50:34 adrian-desktop kernel: [    4.375557] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 25 21:50:34 adrian-desktop kernel: [   12.886810] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 25 21:50:34 adrian-desktop kernel: [  177.093287] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 25 21:50:34 adrian-desktop kernel: [  177.742915] type=1400 audit(1296013834.450:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=917 comm="apparmor_parser"
Jan 25 21:50:37 adrian-desktop kernel: [  180.782066] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 25 21:50:39 adrian-desktop kernel: [  182.716070] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 25 21:57:43 adrian-desktop kernel: [  607.230740] sd 5:0:0:0: Attached scsi generic sg6 type 0
Jan 25 21:57:43 adrian-desktop kernel: [  607.244432] sd 5:0:0:0: [sdf] 1034240 512-byte logical blocks: (529 MB/505 MiB)
Jan 25 21:57:43 adrian-desktop kernel: [  607.244921] sd 5:0:0:0: [sdf] Write Protect is off
Jan 25 21:57:43 adrian-desktop kernel: [  607.248464]  sdf:
Jan 25 21:57:43 adrian-desktop kernel: [  607.251806] sd 5:0:0:0: [sdf] Attached SCSI removable disk
Jan 26 18:03:55 adrian-desktop kernel: [    1.785335] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 26 18:03:55 adrian-desktop kernel: [    1.785528] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 26 18:03:55 adrian-desktop kernel: [    1.785594] sd 0:0:0:0: [sda] Write Protect is off
Jan 26 18:03:55 adrian-desktop kernel: [    1.785623] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 26 18:03:55 adrian-desktop kernel: [    1.785827]  sda:
Jan 26 18:03:55 adrian-desktop kernel: [    1.793253]  sda1 sda2 <
Jan 26 18:03:55 adrian-desktop kernel: [    1.829727]  sda5 >
Jan 26 18:03:55 adrian-desktop kernel: [    1.830025] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 26 18:03:55 adrian-desktop kernel: [    4.116203] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 26 18:03:55 adrian-desktop kernel: [    4.146107] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 26 18:03:55 adrian-desktop kernel: [    4.146247] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 26 18:03:55 adrian-desktop kernel: [    4.146384] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 26 18:03:55 adrian-desktop kernel: [    4.146520] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 26 18:03:55 adrian-desktop kernel: [    4.350608] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 26 18:03:55 adrian-desktop kernel: [    4.361602] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 26 18:03:55 adrian-desktop kernel: [    4.372596] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 26 18:03:55 adrian-desktop kernel: [    4.383594] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 26 18:03:55 adrian-desktop kernel: [   12.974583] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 26 18:03:55 adrian-desktop kernel: [  177.093007] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 26 18:03:55 adrian-desktop kernel: [  177.599374] type=1400 audit(1296086635.306:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=891 comm="apparmor_parser"
Jan 26 18:04:01 adrian-desktop kernel: [  184.246085] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 27 16:35:29 adrian-desktop kernel: [    1.785177] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 27 16:35:29 adrian-desktop kernel: [    1.785372] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 27 16:35:29 adrian-desktop kernel: [    1.785439] sd 0:0:0:0: [sda] Write Protect is off
Jan 27 16:35:29 adrian-desktop kernel: [    1.785468] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 27 16:35:29 adrian-desktop kernel: [    1.785674]  sda:  Magic number: 11:809:553
Jan 27 16:35:29 adrian-desktop kernel: [    1.789795]  sda1 sda2 <
Jan 27 16:35:29 adrian-desktop kernel: [    1.826265]  sda5 >
Jan 27 16:35:29 adrian-desktop kernel: [    1.826564] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 27 16:35:29 adrian-desktop kernel: [    4.095983] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 27 16:35:29 adrian-desktop kernel: [    4.145094] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 27 16:35:29 adrian-desktop kernel: [    4.145271] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 27 16:35:29 adrian-desktop kernel: [    4.145416] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 27 16:35:29 adrian-desktop kernel: [    4.145558] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 27 16:35:29 adrian-desktop kernel: [    4.347591] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 27 16:35:29 adrian-desktop kernel: [    4.358583] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 27 16:35:29 adrian-desktop kernel: [    4.369582] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 27 16:35:29 adrian-desktop kernel: [    4.380576] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 27 16:35:29 adrian-desktop kernel: [   12.967224] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 27 16:35:29 adrian-desktop kernel: [  177.093556] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 27 16:35:29 adrian-desktop kernel: [  177.538819] type=1400 audit(1296167729.247:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=873 comm="apparmor_parser"
Jan 27 16:35:32 adrian-desktop kernel: [  181.011499] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 27 16:35:37 adrian-desktop kernel: [  183.256066] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 27 18:08:27 adrian-desktop kernel: [    1.789170] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 27 18:08:27 adrian-desktop kernel: [    1.789362] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Jan 27 18:08:27 adrian-desktop kernel: [    1.789428] sd 0:0:0:0: [sda] Write Protect is off
Jan 27 18:08:27 adrian-desktop kernel: [    1.789458] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 27 18:08:27 adrian-desktop kernel: [    1.789665]  sda:  Magic number: 11:581:52
Jan 27 18:08:27 adrian-desktop kernel: [    1.793064]  sda1 sda2 <
Jan 27 18:08:27 adrian-desktop kernel: [    1.821198]  sda5 >
Jan 27 18:08:27 adrian-desktop kernel: [    1.821511] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 27 18:08:27 adrian-desktop kernel: [    3.662473] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jan 27 18:08:27 adrian-desktop kernel: [    3.662619] sd 4:0:0:1: Attached scsi generic sg3 type 0
Jan 27 18:08:27 adrian-desktop kernel: [    3.662761] sd 4:0:0:2: Attached scsi generic sg4 type 0
Jan 27 18:08:27 adrian-desktop kernel: [    3.662914] sd 4:0:0:3: Attached scsi generic sg5 type 0
Jan 27 18:08:27 adrian-desktop kernel: [    4.224520] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 27 18:08:27 adrian-desktop kernel: [    4.284817] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jan 27 18:08:27 adrian-desktop kernel: [    4.295814] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Jan 27 18:08:27 adrian-desktop kernel: [    4.306798] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Jan 27 18:08:27 adrian-desktop kernel: [    4.317791] sd 4:0:0:3: [sde] Attached SCSI removable disk
Jan 27 18:08:27 adrian-desktop kernel: [   12.845542] Adding 4142076k swap on /dev/sda5.  Priority:-1 extents:1 across:4142076k 
Jan 27 18:08:27 adrian-desktop kernel: [  219.132678] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 27 18:08:28 adrian-desktop kernel: [  219.295478] type=1400 audit(1296173307.998:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=936 comm="apparmor_parser"
Jan 27 18:08:31 adrian-desktop kernel: [  222.454644] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Jan 27 18:08:33 adrian-desktop kernel: [  224.503631] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

```

---

### Post by TheNerdAL on 2011-01-28
bump

---

