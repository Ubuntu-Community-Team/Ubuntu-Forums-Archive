---
title: "Randomly Unmounts usb driv"
date: 2008-07-14
forum: Hardware
---

### Post by WebDesignHero on 2008-07-14
I have checked a few other posts on similar topics, but they do not match my symptoms exactly.

I have a cavlary 750gb external drive. The filesystem is ntfs (so I think from the last time i formatted it).

Here is the line it adds to mount when it automounts:

> 
/dev/sdb1 on /media/New Volume type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


Now randomly, the drive will just unmount on me. It does not matter if the drive is idle. On numerous occasions I will be watching a video on the drive, and it will just spin down and disable.

Sometimes, the drive will re-automount itself in 3 seconds or so. Sometimes it will remount to /media/New Volume and sometimes to /media/New Volume_ . Last night overnight, it seemed to remount itself over 10 times and go upto /media/New Volume_____________________________ or so. 

This makes using the drive useless. I could understand if this was an issue with the drive going idle and powersaving or something, but its a huge pain to disconnect while watching a movie or listening to music or backingup even with rsync.

Sometimes, it will NOT even remount itself, and plugging/unplugging does not help at all. I have to restart the whole system. This is a huge pain, even when I ran winMe, i only rebooted like once a month. 

I do not really understand how the automounting works here, if its gnome or ubuntu doing it and where the settings are stored. 

I would first and foremost like to get it to stop randomly unmounting. But would also like it to always mount to the same path based on the drive's serial number or something. It makes media library management useless if it mounts to a different location.

Please let me know what other commands to run to give you useful info to help me out.

Dell e1505/6400
Ubuntu 8.04

---

### Post by Daelyn on 2008-07-15
Use the drive, when it unmounts/remounts, do a "dmesg" and paste the last 30-40-50 lines of the result here.
Command:
```
dmesg
```

It will, hopefully, tell us why it dismounts/remounts the device and what happens during the process.

If it also messes up and won't remount etc disconnect, let it settle for a moment and reconnect. Post output of dmesg again. ~fingers crossed~

---

### Post by Embiggens on 2008-07-20
WebDesignHero, I was having perhaps a similar problem, and it appears to be a bad usb connection in my case.

My symptoms were the following: after connecting my usb drive, it automounted to "/media/My\ Book", then after a few minutes or after sometimes trying to access it, it would unmount.  Then it would remount.  So my /media folder would eventually contain an empty "/media/My\ Book", an empty "/media/My\ Book_", and a (temporarily) valid "/media/My\ Book__", etc.  Meanwhile windows with the new mountpoint kept opening on the gnome desktop.  If I looked into dmesg, it would give various 'read' or 'I/O' errors before 'finding' a new device again.

But I just switched to a different connection (same motherboard) and everything's cool.

---

### Post by Daelyn on 2008-07-22
Do wonder what the problem was in the end. Maybe it was a glitchy connection? Let's hope so.

---

### Post by Luke. on 2008-09-16
I seem to be suffering from a similar, if not the same, problem. My dmesg output after umount/remount reads:

```
[54731.346619] usb 2-3: USB disconnect, address 3
[54731.346756] sd 6:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[54731.346765] end_request: I/O error, dev sdc, sector 205406271
[54731.358753] printk: 2 messages suppressed.
[54731.358758] Buffer I/O error on device sdc1, logical block 1289
[54731.358761] lost page write due to I/O error on sdc1
[54731.358813] Buffer I/O error on device sdc1, logical block 1292
[54731.358816] lost page write due to I/O error on sdc1
[54731.358821] Aborting journal on device sdc1.
[54731.358826] Buffer I/O error on device sdc1, logical block 1289
[54731.358828] lost page write due to I/O error on sdc1
[54731.358847] journal commit I/O error
[54731.358872] Buffer I/O error on device sdc1, logical block 25657346
[54731.358875] lost page write due to I/O error on sdc1
[54731.378235] ext3_abort called.
[54731.378245] EXT3-fs error (device sdc1): ext3_journal_start_sb: Detected aborted journal
[54731.378248] Remounting filesystem read-only
[54731.386288] Buffer I/O error on device sdc1, logical block 1289
[54731.386293] lost page write due to I/O error on sdc1
[54738.198062] usb 2-3: new high speed USB device using ehci_hcd and address 4
[54738.330960] usb 2-3: configuration #1 chosen from 1 choice
[54738.331229] scsi7 : SCSI emulation for USB Mass Storage devices
[54738.331372] usb-storage: device found at 4
[54738.331377] usb-storage: waiting for device to settle before scanning
[54743.321036] usb-storage: device scan complete
[54743.321659] scsi 7:0:0:0: Direct-Access     WD       3200BMV External 1.05 PQ: 0 ANSI: 4
[54743.323268] sd 7:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[54743.324260] sd 7:0:0:0: [sdc] Write Protect is off
[54743.324264] sd 7:0:0:0: [sdc] Mode Sense: 21 00 00 00
[54743.324266] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[54743.325633] sd 7:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[54743.326630] sd 7:0:0:0: [sdc] Write Protect is off
[54743.326634] sd 7:0:0:0: [sdc] Mode Sense: 21 00 00 00
[54743.326636] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[54743.326962]  sdc: sdc1
[54743.368719] sd 7:0:0:0: [sdc] Attached SCSI disk
[54743.368872] sd 7:0:0:0: Attached scsi generic sg3 type 0
[54743.608298] kjournald starting.  Commit interval 5 seconds
[54743.613389] EXT3 FS on sdc1, internal journal
[54743.613394] EXT3-fs: recovery complete.
[54743.613399] EXT3-fs: mounted filesystem with ordered data mode.
```

Am I looking at a corrupted disk here? Its an external WD Passport 320GB.

---

