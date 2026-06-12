---
title: "Problems copying media to new external HDD on Blackberry 4 w Ubuntu"
date: 2022-11-29
forum: Hardware
---

### Post by anandamide on 2022-11-29
Hi folks

I run a dinky Pi 4 with Ubuntu 20.04, mostly as a Plex Server. It's hooked up to a rickety 1TB external HDD (with its own power source), which I'm trying to replace with a new 2TB with USB3 connection (drawing power from the Pi).

The old drive is vFAT, the new is ext4

I'm trying to move files accross with a straightforward cp command (latterly cp -nv to keep an eye on things). It generally goes fine for 10 mins or so then crunches to a halt, the new drive disconnecting. I thought maybe this was an issue with cp, and I was better using rsync, but after digging into it that doesn't seem like it should be an issue.

I can keep typing cp -nv for a few days until everything is transferred, but obviously I'd rather know what's going on, especially if it points to any underlying issue with the new drive.

System info and relevent dmesg output follows:

```

uname - a 
Linux blackbird 5.4.0-1074-raspi #85-Ubuntu SMP PREEMPT Fri Nov 4 13:34:24 UTC 2022 aarch64 aarch64 aarch64 GNU/Linux
```

```
df
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/mmcblk0p2 ext4   59G   49G  7.4G  87% /
/dev/mmcblk0p1 vfat  253M  131M  122M  52% /boot/firmware
/dev/sdb2      vfat  1.3T  1.2T  111G  92% /media/ALEXANDRITE
/dev/sda1      ext4  1.8T  754G  987G  44% /media/DIAMOND
```

dmesg from mounting disc and commencing copy to failure. 
n.b. I don't know why it's talking about sdc at the end. The drive doesn't get mounted again until I invoke mount -a, and besides there are only two physical drives attached to it

```

[89285.296456] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[89460.316717] Under-voltage detected! (0x00050005)
[89464.348768] Voltage normalised (0x00000000)
[90042.945395] Under-voltage detected! (0x00050005)
[90043.393325] usb 2-2: USB disconnect, device number 5
[90043.409339] print_req_error: 787 callbacks suppressed
[90043.409345] blk_update_request: I/O error, dev sda, sector 1950624968 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[90043.420406] Aborting journal on device sda1-8.
[90043.424962] blk_update_request: I/O error, dev sda, sector 115444224 op 0x1:(WRITE) flags 0x4000 phys_seg 33 prio class 0
[90043.436152] blk_update_request: I/O error, dev sda, sector 115444736 op 0x1:(WRITE) flags 0x4000 phys_seg 33 prio class 0
[90043.447326] blk_update_request: I/O error, dev sda, sector 3120576768 op 0x1:(WRITE) flags 0x4000 phys_seg 64 prio class 0
[90043.458683] blk_update_request: I/O error, dev sda, sector 1950615552 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[90043.469799] blk_update_request: I/O error, dev sda, sector 1950615552 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[90043.480835] buffer_io_error: 73 callbacks suppressed
[90043.480839] Buffer I/O error on dev sda1, logical block 243826688, lost sync page write
[90043.488973] JBD2: Error -5 detected when updating journal superblock for sda1-8.
[90043.496529] blk_update_request: I/O error, dev sda, sector 2048 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[90043.507062] blk_update_request: I/O error, dev sda, sector 2048 op 0x1:(WRITE) flags 0x800 phys_seg 1 prio class 0
[90043.507115] blk_update_request: I/O error, dev sda, sector 3120577280 op 0x1:(WRITE) flags 0x4000 phys_seg 64 prio class 0
[90043.517565] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[90043.517585] EXT4-fs (sda1): I/O error while writing superblock
[90043.528819] blk_update_request: I/O error, dev sda, sector 115445248 op 0x1:(WRITE) flags 0x4000 phys_seg 33 prio class 0
[90043.536236] EXT4-fs error (device sda1): ext4_journal_check_start:61: Detected aborted journal
[90043.536241] EXT4-fs (sda1): Remounting filesystem read-only
[90043.570159] EXT4-fs warning (device sda1): ext4_end_bio:311: I/O error 10 writing to inode 3145752 (offset 276824064 size 5398528 starting block 14430945)
[90043.570168] buffer_io_error: 32675 callbacks suppressed
[90043.570171] Buffer I/O error on device sda1, logical block 14430208
[90043.576578] Buffer I/O error on device sda1, logical block 14430209
[90043.582964] Buffer I/O error on device sda1, logical block 14430210
[90043.589356] Buffer I/O error on device sda1, logical block 14430211
[90043.595736] Buffer I/O error on device sda1, logical block 14430212
[90043.602110] Buffer I/O error on device sda1, logical block 14430213
[90043.608485] Buffer I/O error on device sda1, logical block 14430214
[90043.614863] Buffer I/O error on device sda1, logical block 14430215
[90043.621261] Buffer I/O error on device sda1, logical block 14430216
[90043.627635] Buffer I/O error on device sda1, logical block 14430217
[90043.635283] EXT4-fs error (device sda1) in ext4_init_inode_table:1460: IO failure
[90043.637204] EXT4-fs error (device sda1) in ext4_reserve_inode_write:6006: Journal has aborted
[90043.643069] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[90043.651664] EXT4-fs warning (device sda1): ext4_end_bio:311: I/O error 10 writing to inode 3145752 (offset 276824064 size 8388608 starting block 14431781)
[90043.659014] EXT4-fs (sda1): I/O error while writing superblock
[90043.659020] EXT4-fs (sda1): previous I/O error to superblock detected
[90043.671579] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[90043.679007] EXT4-fs (sda1): I/O error while writing superblock
[90043.684940] EXT4-fs error (device sda1): mpage_map_and_submit_extent:2624: comm kworker/u8:0: Failed to mark inode 3145752 dirty
[90043.696750] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[90043.704177] EXT4-fs (sda1): I/O error while writing superblock
[90043.710260] EXT4-fs warning (device sda1): ext4_end_bio:311: I/O error 10 writing to inode 3145752 (offset 276824064 size 8388608 starting block 14432512)
[90043.712872] JBD2: Detected IO errors while flushing file data on sda1-8
[90043.712965] Buffer I/O error on dev sda1, logical block 12615698, lost async page write
[90043.721147] Buffer I/O error on dev sda1, logical block 14155781, lost async page write
[90044.863829] JBD2: Error while async write back metadata bh 12615698.
[90044.863965] JBD2: Error while async write back metadata bh 14155781.
[90044.875953] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[90044.882669] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[90045.033754] EXT4-fs error (device sda1): __ext4_find_entry:1577: inode #2: comm pool: reading directory lblock 0
[90045.033759] EXT4-fs error (device sda1): __ext4_find_entry:1577: inode #2: comm pool: reading directory lblock 0
[90045.173807] usb 2-2: new SuperSpeed Gen 1 USB device number 6 using xhci_hcd
[90045.194755] usb 2-2: New USB device found, idVendor=0480, idProduct=0901, bcdDevice= 0.00
[90045.194771] usb 2-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[90045.194782] usb 2-2: Product: EXTERNAL_USB
[90045.194793] usb 2-2: Manufacturer: TOSHIBA
[90045.194803] usb 2-2: SerialNumber: 20220521011383F
[90045.203856] usb-storage 2-2:1.0: USB Mass Storage device detected
[90045.204354] scsi host2: usb-storage 2-2:1.0
[90046.211778] scsi 2:0:0:0: Direct-Access     TOSHIBA  EXTERNAL_USB     0    PQ: 0 ANSI: 6
[90046.214033] sd 2:0:0:0: Attached scsi generic sg0 type 0
[90046.216118] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[90046.216834] sd 2:0:0:0: [sdc] Write Protect is off


```

---

### Post by TheFu on 2022-11-30
So, USB storage sucks.  Connections are flaky.  They have been ... er ... always.  Flaky USB storage happens more often when it isn't powered by external PSU ... a brick.  If you can, get the brick for the USB3 device and power it.

Have to say that I'm confused to see "Blackberry 4" in the thread title. Just came to see what that was about.

BTW, if you want to copy all the files from /media/ALEXANDRITE ----> /media/DIAMOND, and there is more than 10, use rsync.

```

rsync --progress    --stats    -av    /media/ALEXANDRITE/   /media/DIAMOND 
```
I think that will do it.  If there is any failure, run exactly the same command again and again and again and again, until it finishes.  If the source wasn't FAT-whatever, but a native Linux file system, then I'd use sudo to retain the owners, groups, permissions, xattrs and complex ACLs ... but with FAT-whatever, those things don't exist.

If nothing is showing up on  /media/DIAMOND, then run (literally copy/paste that command as is)
```
sudo chown -R $USER  /media/DIAMOND
```
to make your userid the owner of all files. From that point on, you won't need sudo on that storage, unless you use sudo to screw it up.

---

