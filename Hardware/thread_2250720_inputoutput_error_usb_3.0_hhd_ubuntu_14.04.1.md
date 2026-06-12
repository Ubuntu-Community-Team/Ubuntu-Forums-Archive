---
title: "input/output error usb 3.0 hhd ubuntu 14.04.1"
date: 2014-10-30
forum: Hardware
---

### Post by mveirup on 2014-10-30
Hey

After 6-9 hours reporting the system gives input/output errors - but after a restart the hhd works again for 6-9 hours.

any idea how to avoid this?

System:
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty


lsusb:
media@server:~$ lsusb
Bus 002 Device 006: ID 1c73:861f AMT Anysee E30 USB 2.0 DVB-T Receiver
Bus 002 Device 005: ID 1c73:861f AMT Anysee E30 USB 2.0 DVB-T Receiver
Bus 002 Device 004: ID 1c73:861f AMT Anysee E30 USB 2.0 DVB-T Receiver
Bus 002 Device 003: ID 1c73:861f AMT Anysee E30 USB 2.0 DVB-T Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 152d:0551 JMicron Technology Corp. / JMicron USA Technology Corp.
Bus 004 Device 002: ID 152d:0539 JMicron Technology Corp. / JMicron USA Technology Corp. JMS539 SuperSpeed SATA II 3.0G Bridge
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg -last part
[10149.962696] sd 5:0:0:0: Device offlined - not ready after error recovery
[10149.965614] sd 5:0:0:0: [sdc] Unhandled error code
[10149.965619] sd 5:0:0:0: [sdc]
[10149.965621] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[10149.965623] sd 5:0:0:0: [sdc] CDB:
[10149.965625] Write(16): 8a 00 00 00 00 00 4f 5f 07 fe 00 00 00 f0 00 00
[10149.965635] end_request: I/O error, dev sdc, sector 1331628030
[10149.965673] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453533)
[10149.965676] Buffer I/O error on device sdc1, logical block 166453248
[10149.965711] Buffer I/O error on device sdc1, logical block 166453249
[10149.965743] Buffer I/O error on device sdc1, logical block 166453250
[10149.965774] Buffer I/O error on device sdc1, logical block 166453251
[10149.965805] Buffer I/O error on device sdc1, logical block 166453252
[10149.965837] Buffer I/O error on device sdc1, logical block 166453253
[10149.965868] Buffer I/O error on device sdc1, logical block 166453254
[10149.965899] Buffer I/O error on device sdc1, logical block 166453255
[10149.965930] Buffer I/O error on device sdc1, logical block 166453256
[10149.965961] Buffer I/O error on device sdc1, logical block 166453257
[10149.966013] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453593)
[10149.966034] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453623)
[10149.966054] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453653)
[10149.966071] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453683)
[10149.966088] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453713)
[10149.966106] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453743)
[10149.966122] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453773)
[10149.966140] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453803)
[10149.966157] EXT4-fs warning (device sdc1): ext4_end_bio:317: I/O error -5 writing to inode 137429015 (offset 0 size 8388608 starting block 166453833)
[10149.967646] Aborting journal on device sdc1-8.
[10149.967747] JBD2: Error -5 detected when updating journal superblock for sdc1-8.
[10149.967761] EXT4-fs (sdc1): Delayed block allocation failed for inode 137429015 at logical offset 4096 with max blocks 2048 with error 30
[10149.967762] EXT4-fs (sdc1): This should not happen!! Data will be lost
[10149.967762]
[10149.967764] EXT4-fs error (device sdc1) in ext4_writepages:2567: Journal has aborted
[10149.967947] EXT4-fs (sdc1): previous I/O error to superblock detected
[10149.967985] EXT4-fs error (device sdc1): ext4_journal_check_start:56: Detected aborted journal
[10149.968031] EXT4-fs (sdc1): Remounting filesystem read-only
[10149.968059] EXT4-fs (sdc1): previous I/O error to superblock detected
[10149.968096] EXT4-fs error (device sdc1) in ext4_da_write_end:2812: IO failure
[10149.968131] EXT4-fs (sdc1): previous I/O error to superblock detected
[10149.968700] sd 5:0:0:0: [sdc] Unhandled error code
[10149.968703] sd 5:0:0:0: [sdc]
[10149.968705] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[10149.968707] sd 5:0:0:0: [sdc] CDB:
[10149.968708] Write(16): 8a 00 00 00 00 00 4f 5f 08 ee 00 00 00 f0 00 00
[10149.968717] end_request: I/O error, dev sdc, sector 1331628270
[10150.644752] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036b47e00
[10150.644757] xhci_hcd 0000:03:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880036b47e40
[10161.023424] EXT4-fs error (device sdc1): ext4_find_entry:1309: inode #137428993: comm rsync: reading directory lblock 0
[10178.027712] perf samples too long (2535 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[15085.203544] EXT4-fs error (device sdc1): ext4_find_entry:1309: inode #137428993: comm rsync: reading directory lblock 0
[17986.326117] EXT4-fs error (device sdc1): ext4_find_entry:1309: inode #137428993: comm rsync: reading directory lblock 0
[21604.357220] EXT4-fs warning: 128 callbacks suppressed
[21604.357231] EXT4-fs warning (device sdc1): __ext4_read_dirblock:908: error re       



/etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cfd3ce48-34de-4c2f-bba1-54e749773bc8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c0f91d8c-bb92-4932-ad98-0dde95d09518 none            swap    sw              0       0
UUID=8c4112a9-a9f8-4e20-9e99-586685524c32 /home/media/XXXXXXXXX ext4 defaults 0    0
UUID=76dff76a-2e0c-4ad7-b5f6-0b5e1f13a7e9 /home/media/XXXXX ext4 defaults 0  0
//192.168.0.1/backup  /home/media/XXXXXXX cifs username=XXXXXXXX,password=XXXXXXXXXXXXXXXX,rw

---

