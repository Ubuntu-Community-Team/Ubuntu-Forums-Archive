---
title: "Mounting a hfsplus file system"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by carlinuxlearner on 2008-01-17
I'm not sure weather this post should be here but I couldn't find a better place.
Ok I am trying to copy files off of this HD and it was out of a MAC so it has the hfsplus file system, however every time I mount it, it mounts as a "read only" file system, and some folders on it can't be opened due to permissions, so I CAN"T copy them and I NEED to, so what can I do?? I CANNOT change the files permissions, OR owner, because it's "read only" so every time try it won't let me!!! so can I SAFELY mount it as a writable file system, and then go change the permissions? And (if so) HOW!!!!
Or could some one just tell me how to AS ROOT, cd to the directory, and get the files and copy them to a DVD.

C@RL

---

### Post by Yellow Pasque on 2008-01-17
Did you mount as root?
```
sudo mount -t -o uid=100 hfsplus /dev/<device>  /<dirpath you want to mount to>
```
> Mount options for hfs
       creator=cccc, type=cccc
              Set the creator/type values as shown by the MacOS finder used  for  creating
              new files.  Default values: '????'.

       uid=n, gid=n
              Set the owner and group of all files.  (Default: the uid and gid of the cur-
              rent process.)

       dir_umask=n, file_umask=n, umask=n
              Set the umask used for all directories, all regular files, or all files  and
              directories.  Defaults to the umask of the current process.

---

### Post by carlinuxlearner on 2008-01-18
"sudo mount -t -o uid=100 hfsplus /dev/<device>  /<dirpath you want to mount to>"

already tried that, it didn't work. (But thanks for the suggestion)
I did succeed in copying the files, I booted up in recovery mode, started "X", and since I was running as root I could see all the files and copy them. 

C@RL

---

### Post by tgalati4 on 2008-01-18
You need to use Disk Utility on the mac and turn off journaling.  The hfs+ kernel driver works on an unjournaled file system, unfortunately.  Once journaling is turned off it should mount as rw then and everyone is happy again.

When you are done, you can turn journaling back on once hooked back up to the mac.

---

### Post by click170 on 2008-02-02
Hello all,

I'm trying to mount an external hard drive which has been partitioned into three different parts and each is partitioned with HFS+ (Journaled).  I'm trying to mount them in Ubuntu, but am not having any luck.  I read the previous post's suggestion about disabling journaling from Apple's Disk Utility but there doesn't seem to be any such option (In Leopard?).  

When I plug it in (via firewire), it doesn't seem to be able to read the partition table.  
This is the output from `fdisk -l` when I'm trying to figure out what the heck.

Disk /dev/sdi: 1000.2 GB, 1000215674880 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdi doesn't contain a valid partition table


At first I figured I had to load some HFSplus module, but that didn't seem like it.  Am I doing something wrong?  

At the bottom is the relevant output from my syslog, any help at all would be appreciated.  With regards to the timestamp, the last few messages were created when I removed the device.


Feb  2 11:41:23 Shmee kernel: [483194.391558] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
Feb  2 11:41:23 Shmee kernel: [483194.391573] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
Feb  2 11:41:23 Shmee kernel: [483194.393716] printk: 21 messages suppressed.
Feb  2 11:41:23 Shmee kernel: [483194.393718] rtc: lost 1 interrupts
Feb  2 11:41:23 Shmee kernel: [483194.663418] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[00d04b781a0325ac]
Feb  2 11:41:23 Shmee kernel: [483194.663447] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Feb  2 11:41:23 Shmee kernel: [483194.663574] scsi12 : SBP-2 IEEE-1394
Feb  2 11:41:24 Shmee kernel: [483195.699386] ieee1394: sbp2: Logged into SBP-2 device
Feb  2 11:41:24 Shmee kernel: [483195.699786] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [1024]
Feb  2 11:41:24 Shmee kernel: [483195.701603] scsi 12:0:1:0: Direct-Access     LaCie    BigDisk Extreme+ CR10 PQ: 0 ANSI: 4
Feb  2 11:41:24 Shmee kernel: [483195.702932] sd 12:0:1:0: [sdi] 1953546240 512-byte hardware sectors (1000216 MB)
Feb  2 11:41:24 Shmee kernel: [483195.703787] sd 12:0:1:0: [sdi] Write Protect is off
Feb  2 11:41:24 Shmee kernel: [483195.703790] sd 12:0:1:0: [sdi] Mode Sense: 10 00 00 00
Feb  2 11:41:24 Shmee kernel: [483195.704446] sd 12:0:1:0: [sdi] Cache data unavailable
Feb  2 11:41:24 Shmee kernel: [483195.704449] sd 12:0:1:0: [sdi] Assuming drive cache: write through
Feb  2 11:41:24 Shmee kernel: [483195.705771] sd 12:0:1:0: [sdi] 1953546240 512-byte hardware sectors (1000216 MB)
Feb  2 11:41:24 Shmee kernel: [483195.706576] sd 12:0:1:0: [sdi] Write Protect is off
Feb  2 11:41:24 Shmee kernel: [483195.706579] sd 12:0:1:0: [sdi] Mode Sense: 10 00 00 00
Feb  2 11:41:24 Shmee kernel: [483195.707219] sd 12:0:1:0: [sdi] Cache data unavailable
Feb  2 11:41:24 Shmee kernel: [483195.707221] sd 12:0:1:0: [sdi] Assuming drive cache: write through
Feb  2 11:41:24 Shmee kernel: [483195.707224]  sdi:<6>ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.724788] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.724793] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.740189] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.740196] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.740200] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.755551] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.755558] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.755562] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.755579]  unknown partition table
Feb  2 11:41:24 Shmee kernel: [483195.755618] sd 12:0:1:0: [sdi] Attached SCSI disk
Feb  2 11:41:24 Shmee kernel: [483195.755663] sd 12:0:1:0: Attached scsi generic sg9 type 0
Feb  2 11:41:24 Shmee kernel: [483195.914901] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.914912] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.914915] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.930319] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.930326] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.930328] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.945670] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.945679] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.945682] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.961083] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.961090] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.961093] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.981752] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.981760] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.981764] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:24 Shmee kernel: [483195.997148] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:24 Shmee kernel: [483195.997156] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:24 Shmee kernel: [483195.997160] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.012571] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.012580] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.012584] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee NetworkManager: <debug> [1201981285.011766] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ieee1394_guid_d04b781a0325ac_0_scsi_host'). 
Feb  2 11:41:25 Shmee NetworkManager: <debug> [1201981285.015288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ieee1394_guid_d04b781a0325ac_0_scsi_host_scsi_device_lun0'). 
Feb  2 11:41:25 Shmee NetworkManager: <debug> [1201981285.015798] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/ieee1394_guid_d04b781a0325ac_0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb  2 11:41:25 Shmee kernel: [483196.031185] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.031196] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.031199] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.052995] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.053005] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.053009] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.073638] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.073646] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.073650] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.108372] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.108380] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.108384] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.127033] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.127042] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.127046] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.142395] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.142403] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.142407] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.157822] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.157830] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.157833] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.173225] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.173233] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.173236] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.193823] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.193830] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.193834] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.207658] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.207665] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.207668] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.223020] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.223028] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.223031] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.236818] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.236825] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.236829] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.252227] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.252235] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.252238] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.267589] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.267597] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.267600] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.288243] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.288250] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.288253] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee kernel: [483196.303691] ieee1394: sbp2: resp 0x1, sbp_status 0x4e
Feb  2 11:41:25 Shmee kernel: [483196.303699] sd 12:0:1:0: [sdi] Sense Key : No Sense [current] 
Feb  2 11:41:25 Shmee kernel: [483196.303702] sd 12:0:1:0: [sdi] Add. Sense: No additional sense information
Feb  2 11:41:25 Shmee NetworkManager: <debug> [1201981285.300699] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_00d04b781a0325ac_1_0'). 
Feb  2 11:43:47 Shmee kernel: [483337.965008] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Feb  2 11:43:47 Shmee kernel: [483337.965015] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[00d04b781a0325ac]
Feb  2 11:43:47 Shmee NetworkManager: <debug> [1201981427.175865] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ieee1394_guid_d04b781a0325ac_0_scsi_host_scsi_device_lun0_scsi_generic'). 
Feb  2 11:43:47 Shmee NetworkManager: <debug> [1201981427.178843] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_00d04b781a0325ac_1_0'). 
Feb  2 11:43:47 Shmee NetworkManager: <debug> [1201981427.178903] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ieee1394_guid_d04b781a0325ac_0_scsi_host_scsi_device_lun0'). 
Feb  2 11:43:47 Shmee NetworkManager: <debug> [1201981427.178940] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/ieee1394_guid_d04b781a0325ac_0_scsi_host').

---

