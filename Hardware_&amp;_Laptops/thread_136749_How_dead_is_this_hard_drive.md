---
title: "How dead is this hard drive?"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by Velvet Elvis on 2006-02-26
Ok, I started getting SMART errors on the last couple of reboots so I started moving data off the drive.  I was halfway done when the drive seemingly unmounted itself and ceased to exist.   When the journals are replayed on reboot I get lots of I/O errors before chkreiserfs quits (with error 18, I think.)

I set /dev/hdb -a in /etc/smartd.conf.  here is what I get in /var/log/messages when I try to manualy mount the drive:
```


Feb 26 15:33:27 localhost kernel: [4296252.650000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:27 localhost kernel: [4296252.650000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=7864383, sector=7864383
Feb 26 15:33:27 localhost kernel: [4296252.650000] ide: failed opcode was: unknown
Feb 26 15:33:29 localhost kernel: [4296254.216000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:29 localhost kernel: [4296254.217000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=7864383, sector=7864383
Feb 26 15:33:29 localhost kernel: [4296254.217000] ide: failed opcode was: unknown
Feb 26 15:33:29 localhost kernel: [4296254.217000] end_request: I/O error, dev hdb, sector 7864383
Feb 26 15:33:29 localhost kernel: [4296254.218000] ReiserFS: hdb1: warning: sh-2029: reiserfs read_bitmaps: bitmap block (#983040) reading failed
Feb 26 15:33:29 localhost kernel: [4296254.218000] ReiserFS: hdb1: warning: jmacd-8: reiserfs_fill_super: unable to read bitmap
Feb 26 15:33:31 localhost kernel: [4296256.207000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:31 localhost kernel: [4296256.207000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=15466559, sector=15466559
Feb 26 15:33:31 localhost kernel: [4296256.207000] ide: failed opcode was: unknown
Feb 26 15:33:31 localhost kernel: [4296256.207000] end_request: I/O error, dev hdb, sector 15466559
Feb 26 15:33:32 localhost kernel: [4296258.115000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:33 localhost kernel: [4296258.115000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=15728703, sector=15728703
Feb 26 15:33:33 localhost kernel: [4296258.115000] ide: failed opcode was: unknown
Feb 26 15:33:33 localhost kernel: [4296258.115000] end_request: I/O error, dev hdb, sector 15728703
Feb 26 15:33:34 localhost kernel: [4296259.973000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:34 localhost kernel: [4296259.973000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:34 localhost kernel: [4296259.973000] ide: failed opcode was: unknown
Feb 26 15:33:35 localhost kernel: [4296261.147000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:35 localhost kernel: [4296261.147000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:35 localhost kernel: [4296261.147000] ide: failed opcode was: unknown
Feb 26 15:33:37 localhost kernel: [4296262.313000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:38 localhost kernel: [4296262.313000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:38 localhost kernel: [4296262.313000] ide: failed opcode was: unknown
Feb 26 15:33:38 localhost kernel: [4296263.738000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:38 localhost kernel: [4296263.738000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:38 localhost kernel: [4296263.738000] ide: failed opcode was: unknown
Feb 26 15:33:38 localhost kernel: [4296264.088000] ide0: reset: success
Feb 26 15:33:40 localhost kernel: [4296265.462000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:40 localhost kernel: [4296265.462000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:40 localhost kernel: [4296265.462000] ide: failed opcode was: unknown
Feb 26 15:33:41 localhost kernel: [4296266.628000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:41 localhost kernel: [4296266.628000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:41 localhost kernel: [4296266.628000] ide: failed opcode was: unknown
Feb 26 15:33:42 localhost kernel: [4296268.011000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:42 localhost kernel: [4296268.011000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:42 localhost kernel: [4296268.011000] ide: failed opcode was: unknown
Feb 26 15:33:44 localhost kernel: [4296269.386000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:44 localhost kernel: [4296269.386000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:44 localhost kernel: [4296269.386000] ide: failed opcode was: unknown
Feb 26 15:33:44 localhost kernel: [4296269.736000] ide0: reset: success
Feb 26 15:33:45 localhost kernel: [4296270.902000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:45 localhost kernel: [4296270.902000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=28835903, sector=28835903
Feb 26 15:33:45 localhost kernel: [4296270.902000] ide: failed opcode was: unknown
Feb 26 15:33:45 localhost kernel: [4296270.902000] end_request: I/O error, dev hdb, sector 28835903
Feb 26 15:33:46 localhost kernel: [4296272.068000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:48 localhost kernel: [4296272.068000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29098047, sector=29098047
Feb 26 15:33:48 localhost kernel: [4296272.068000] ide: failed opcode was: unknown
Feb 26 15:33:48 localhost kernel: [4296273.434000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:48 localhost kernel: [4296273.434000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29098047, sector=29098047
Feb 26 15:33:48 localhost kernel: [4296273.434000] ide: failed opcode was: unknown
Feb 26 15:33:49 localhost kernel: [4296275.067000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:49 localhost kernel: [4296275.067000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=29098047, sector=29098047
Feb 26 15:33:49 localhost kernel: [4296275.067000] ide: failed opcode was: unknown
Feb 26 15:33:49 localhost kernel: [4296275.067000] end_request: I/O error, dev hdb, sector 29098047
Feb 26 15:33:51 localhost kernel: [4296276.233000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:51 localhost kernel: [4296276.233000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29360191, sector=29360191
Feb 26 15:33:51 localhost kernel: [4296276.233000] ide: failed opcode was: unknown
Feb 26 15:33:52 localhost kernel: [4296277.657000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:54 localhost kernel: [4296277.657000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=29360191, sector=29360191
Feb 26 15:33:54 localhost kernel: [4296277.657000] ide: failed opcode was: unknown
Feb 26 15:33:54 localhost kernel: [4296277.657000] end_request: I/O error, dev hdb, sector 29360191
Feb 26 15:33:54 localhost kernel: [4296279.282000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:54 localhost kernel: [4296279.282000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=29622335, sector=29622335
Feb 26 15:33:54 localhost kernel: [4296279.282000] ide: failed opcode was: unknown
Feb 26 15:33:54 localhost kernel: [4296279.282000] end_request: I/O error, dev hdb, sector 29622335
Feb 26 15:33:55 localhost kernel: [4296280.656000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:55 localhost kernel: [4296280.656000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29884479, sector=29884479
Feb 26 15:33:55 localhost kernel: [4296280.656000] ide: failed opcode was: unknown
Feb 26 15:33:56 localhost kernel: [4296281.599000] IN=ppp0 OUT= MAC= SRC=209.244.16.217 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=64209 PROTO=2
Feb 26 15:33:56 localhost kernel: [4296282.022000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:56 localhost kernel: [4296282.022000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29884479, sector=29884479
Feb 26 15:33:56 localhost kernel: [4296282.022000] ide: failed opcode was: unknown
Feb 26 15:33:58 localhost kernel: [4296283.405000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:58 localhost kernel: [4296283.405000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29884479, sector=29884479
Feb 26 15:33:58 localhost kernel: [4296283.405000] ide: failed opcode was: unknown
Feb 26 15:33:59 localhost kernel: [4296284.771000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:33:59 localhost kernel: [4296284.771000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29884479, sector=29884479
Feb 26 15:33:59 localhost kernel: [4296284.771000] ide: failed opcode was: unknown
Feb 26 15:33:59 localhost kernel: [4296285.121000] ide0: reset: success
Feb 26 15:34:01 localhost kernel: [4296286.287000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:34:02 localhost kernel: [4296286.287000] hdb: task_in_intr: error=0x01 { AddrMarkNotFound }, LBAsect=29884479, sector=29884479
Feb 26 15:34:02 localhost kernel: [4296286.287000] ide: failed opcode was: unknown
Feb 26 15:34:02 localhost kernel: [4296288.078000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
Feb 26 15:34:02 localhost kernel: [4296288.078000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=29884479, sector=29884479
Feb 26 15:34:02 localhost kernel: [4296288.078000] ide: failed opcode was: unknown
Feb 26 15:34:02 localhost kernel: [4296288.078000] end_request: I/O error, dev hdb, sector 29884479

```

Any suggestions on getting my data off?  Would this drive be safe to use if reformatted or is it just gone?

---

### Post by rory_fireshaper on 2006-02-26
Try putting it in the freezer for a day. Sometimes this will give you enough time to get what you need off of a drive before it does forever. I've seen drives last another 2-3 days after being put in the freezer.

---

### Post by mjwood0 on 2006-02-26
:confused: :confused: Umm...  Can I play my ignorance here and ask how in the world freezing the drive helps it?  I'm not doubting you here, but I've been in the computer world a while and never heard this...

---

### Post by WildTangent on 2006-02-27
I've heard about this method before, and although I personally can't say it works, but what will you loose by trying? The drive already seems dead...

-Wild

---

### Post by teet on 2006-02-27
I work part time in a computer shop in the summers...one of the other technicians used the "old harddrive in the freezer" trick.  It worked.

She took it out of the freezer (I assume she had it in a ziplock bag or something), and immediately hooked it up.  She then used acronis true image to copy the data to a new harddrive.

BTW, the customer was a lawyer and he had all sorts of important legal documents on his harddrive (not backed up of course)...beats the heck out of paying a couple grand to have a professional service (like OnTrack) get your data back.

-teet

Edit:  I should at least note that freezing your harddrive should be your last resort, and you should always go into it assuming that you're going to have a new paperweight (or a couple of really good magnets if you open it up!).

---

### Post by mjwood0 on 2006-02-27
Well, ya learn something new every day. 

Still not sure i understand why this works, but hey!  You take what you can get!

---

### Post by wrtrdood on 2006-02-27
If you've been getting S.M.A.R.T. errors then it's likely that the drive is history.  Just got this on a Toshiba laptop drive myself but it's pretty definite.  I got that "imminent failure" message on boot.

When a drive starts spewing S.M.A.R.T. messages it's close to being toast.  You may be out of luck at this point.  Here's a blurb on this technology for others that may wonder what it does:

[I]S.M.A.R.T. monitors disk performance, faulty sectors, recalibration, CRC errors, drive spin-up time, drive heads, distance between the heads and the disk platters, drive temperature, and characteristics of the media, motor and servomechanisms. The errors the system can detect can be predicted by a number of methods. Currently the SMART system can detect about 70% of all hard drive errors.
[/I]


Given that, it's wise to immediately back up important data.  You may not get another chance.

---

### Post by asm2000 on 2007-05-06
for me also same problem or may be different sure i don not know.but i have 2 ide hard disks the problem with both while trying to install ubuntu however i have good working xp and vista..

hda:max request size:128 kib
hda:156301488 sectors(80026 mb) w/2048 kib cache 
chs=65535/16/63,UDMA(100)
HDA CACHE FLUSHES SUPPORTD.

hda:hda:dma_intr:status=0x51{drive ready seek complete error}
hda:dma_intr:error=0x84{drive status error bad CRC}
ide:failed opcode was:unknown

---

