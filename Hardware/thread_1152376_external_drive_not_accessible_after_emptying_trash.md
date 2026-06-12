---
title: "external drive not accessible after emptying trash"
date: 2009-05-07
forum: Hardware
---

### Post by kdib on 2009-05-07
This is my first post so firstly; hello everyone and thanks for all the great posts! Love Ubuntu, love the community :) All too happy to finally put Windows behind me...

I have been using Ubuntu 8.10 (x86 currently using 2.6.27-11-generic) with my USB drive as backup for the last year without issue. Yesterday when I went to make a USB Startup Disk on a thumb drive it all went wrong for me.

I had both USB drives plugged in and copied files from thumb drive (Kingston DataTraveler 4GB) to external (Fantom Drives USB [WD Caviar SATA 500GB NTFS]) drive. Once done; I went back to the thumb drive and deleted files; then emptied trash as my 36GB raptors fill up quick.

Upon doing that, once trash was emptied, I immediately got an error about 'EXTERNAL' having been deleted which was quite a scare. It seemed to unmount itself and since then just repeats mounting, unmounting, remounting over and over again.

I've booted into XP and the 'removable hardware' icon in sys tray mounts it, unmounts it, mounts it repeatedly within seconds. I tried running chkdsk but it doesn't seem to find the drive before loading the desktop so no help there. While in desktop it doesn't stay connected long enough to do anything with it; like 'properly removing' for instance.

I should mention that when rebooting, POST hangs for a long while (as though it's arguing with the external drive); then boots as usual. I've rebooted with the drive powered on many of times and never experienced this so that must be something to do with the problem...

I've tried connecting to my laptop with same results in both XP/Ubuntu. I've changed USB ports, same problem. Back to Ubuntu on my desktop...

I get the following errors:

First popup message:
Could not display "/media/EXTERNAL".
Error: Error stating file '/media/EXTERNAL': Input/output error
Please select another viewer and try again.

Second popup message:
Could not find "/media/EXTERNAL".
Please check the spelling and try again.

Third popup message:
Unable to mount EXTERNAL
DBus error org.freedesktop.DBus.Error.NoReply:
Did not receive a reply. Possible causes include:
the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

When I click OK on these errors, I see the volume mounted for a moment and Nautilus even opens the directory and I see all my files for a second; then poof... unmounted and the process repeats itself.

```


WOPR ~: lsusb
Bus 008 Device 002: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp.
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 003: ID 045e:00dd Microsoft Corp.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

WOPR ~: mount | grep '/dev/'
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)

May  7 09:03:49 WOPR -- MARK --
May  7 09:06:22 WOPR kernel: [66168.340020] usb 8-2: new high speed USB device using ehci_hcd and address 3
May  7 09:06:22 WOPR kernel: [66168.473401] usb 8-2: configuration #1 chosen from 1 choice
May  7 09:06:22 WOPR kernel: [66168.474476] scsi7 : SCSI emulation for USB Mass Storage devices
May  7 09:06:22 WOPR kernel: [66168.475354] usb-storage: device found at 3
May  7 09:06:22 WOPR kernel: [66168.475360] usb-storage: waiting for device to settle before scanning
May  7 09:06:27 WOPR kernel: [66173.473764] usb-storage: device scan complete
May  7 09:06:27 WOPR kernel: [66173.474253] scsi 7:0:0:0: Direct-Access     WDC WD50 00AAKS-22YGA0         PQ: 0 ANSI: 2 CCS
May  7 09:06:27 WOPR kernel: [66173.475598] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
May  7 09:06:27 WOPR kernel: [66173.476098] sd 7:0:0:0: [sdc] Write Protect is off
May  7 09:06:27 WOPR kernel: [66173.476107] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
May  7 09:06:27 WOPR kernel: [66173.476110] sd 7:0:0:0: [sdc] Assuming drive cache: write through
May  7 09:06:27 WOPR kernel: [66173.476721] sd 7:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
May  7 09:06:27 WOPR kernel: [66173.477226] sd 7:0:0:0: [sdc] Write Protect is off
May  7 09:06:27 WOPR kernel: [66173.477232] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
May  7 09:06:27 WOPR kernel: [66173.477235] sd 7:0:0:0: [sdc] Assuming drive cache: write through
May  7 09:06:27 WOPR kernel: [66173.477239]  sdc: sdc1
May  7 09:06:27 WOPR kernel: [66173.491703] sd 7:0:0:0: [sdc] Attached SCSI disk
May  7 09:06:27 WOPR kernel: [66173.491836] sd 7:0:0:0: Attached scsi generic sg3 type 0
May  7 09:06:28 WOPR ntfs-3g[25644]: Version 1.2506 external FUSE 27 
May  7 09:06:28 WOPR ntfs-3g[25644]: Mounted /dev/sdc1 (Read-Write, label "EXTERNAL", NTFS 3.1) 
May  7 09:06:28 WOPR ntfs-3g[25644]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
May  7 09:06:28 WOPR ntfs-3g[25644]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096 
May  7 09:06:28 WOPR hald: mounted /dev/sdc1 on behalf of uid 1000
May  7 09:06:28 WOPR kernel: [66174.805865] usb 8-2: USB disconnect, address 3
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR kernel: [66174.806023] sd 7:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR kernel: [66174.806031] end_request: I/O error, dev sdc, sector 6504519
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR kernel: [66174.806038] Buffer I/O error on device sdc1, logical block 813057
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR kernel: [66174.806420] Buffer I/O error on device sdc1, logical block 813057
May  7 09:06:28 WOPR kernel: [66174.806948] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR kernel: [66174.806961] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR kernel: [66174.807270] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR kernel: [66174.808093] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR kernel: [66174.808293] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR kernel: [66174.808464] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR kernel: [66174.808613] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR kernel: [66174.808746] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: Error reading $Mft record(s): Input/output error
May  7 09:06:28 WOPR ntfs-3g[25644]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:28 WOPR hald[6222]: forcibly attempting to lazy unmount /dev/sdc1 as enclosing drive was disconnected
May  7 09:06:28 WOPR ntfs-3g[25644]: Unmounting /dev/sdc1 (EXTERNAL) 
May  7 09:06:28 WOPR hald: unmounted /dev/sdc1 from '/media/EXTERNAL' on behalf of uid 0
May  7 09:06:35 WOPR kernel: [66181.380012] usb 8-2: new high speed USB device using ehci_hcd and address 4
May  7 09:06:35 WOPR kernel: [66181.520819] usb 8-2: configuration #1 chosen from 1 choice
May  7 09:06:35 WOPR kernel: [66181.521260] scsi8 : SCSI emulation for USB Mass Storage devices
May  7 09:06:35 WOPR kernel: [66181.521337] usb-storage: device found at 4
May  7 09:06:35 WOPR kernel: [66181.521342] usb-storage: waiting for device to settle before scanning
May  7 09:06:40 WOPR kernel: [66186.520389] usb-storage: device scan complete
May  7 09:06:40 WOPR kernel: [66186.520840] scsi 8:0:0:0: Direct-Access     WDC WD50 00AAKS-22YGA0         PQ: 0 ANSI: 2 CCS
May  7 09:06:40 WOPR kernel: [66186.522568] sd 8:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
May  7 09:06:40 WOPR kernel: [66186.523062] sd 8:0:0:0: [sdc] Write Protect is off
May  7 09:06:40 WOPR kernel: [66186.523067] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00
May  7 09:06:40 WOPR kernel: [66186.523070] sd 8:0:0:0: [sdc] Assuming drive cache: write through
May  7 09:06:40 WOPR kernel: [66186.523687] sd 8:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
May  7 09:06:40 WOPR kernel: [66186.524183] sd 8:0:0:0: [sdc] Write Protect is off
May  7 09:06:40 WOPR kernel: [66186.524186] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00
May  7 09:06:40 WOPR kernel: [66186.524188] sd 8:0:0:0: [sdc] Assuming drive cache: write through
May  7 09:06:40 WOPR kernel: [66186.524198]  sdc: sdc1
May  7 09:06:40 WOPR kernel: [66186.527718] sd 8:0:0:0: [sdc] Attached SCSI disk
May  7 09:06:40 WOPR kernel: [66186.527833] sd 8:0:0:0: Attached scsi generic sg3 type 0
May  7 09:06:41 WOPR ntfs-3g[25730]: Version 1.2506 external FUSE 27 
May  7 09:06:41 WOPR hald: mounted /dev/sdc1 on behalf of uid 1000
May  7 09:06:41 WOPR ntfs-3g[25730]: Mounted /dev/sdc1 (Read-Write, label "EXTERNAL", NTFS 3.1) 
May  7 09:06:41 WOPR ntfs-3g[25730]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
May  7 09:06:41 WOPR ntfs-3g[25730]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,fsname=/dev/sdc1,blkdev,blksize=4096 
May  7 09:06:41 WOPR kernel: [66187.892454] usb 8-2: USB disconnect, address 4
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.892607] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.892615] end_request: I/O error, dev sdc, sector 6504519
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.892620] __ratelimit: 11 callbacks suppressed
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR kernel: [66187.892628] Buffer I/O error on device sdc1, logical block 813057
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.892691] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.892696] end_request: I/O error, dev sdc, sector 6504519
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.892700] Buffer I/O error on device sdc1, logical block 813057
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR kernel: [66187.893711] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.893724] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.894240] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR kernel: [66187.894510] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR kernel: [66187.894816] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: Error reading $Mft record(s): Input/output error
May  7 09:06:41 WOPR ntfs-3g[25730]: ntfs_mft_record_read failed: Input/output error
May  7 09:06:41 WOPR hald[6222]: forcibly attempting to lazy unmount /dev/sdc1 as enclosing drive was disconnected
May  7 09:06:41 WOPR kernel: [66187.895483] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR kernel: [66187.895761] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR kernel: [66187.896051] Buffer I/O error on device sdc1, logical block 786433
May  7 09:06:41 WOPR ntfs-3g[25730]: Unmounting /dev/sdc1 (EXTERNAL) 
May  7 09:06:41 WOPR hald: unmounted /dev/sdc1 from '/media/EXTERNAL' on behalf of uid 0
REPEATS...


```The external drive is less than 1.5 years old and so, although possible, would be quite an unexpected coinsidence to die on me during this operation. Not that I think emptying my trash should cause any issues but here I am...

At this point I'm aware of two options I can try:

I can attempt to force mount it. But then (as I've read) I could worsen the situation regarding permissions. Since I can't see the drive I'm not sure how I would go about forcing it to mount in the first place though.

The other option (already out-of-warranty) is to crack open the enclosure and stick the drive in my case on SATA channel although I have no clue if this will make a difference.

Beyond that I'm lost and really don't want to accept the drive just died as that is ALL my (supposedly) backed up data. The better part of a decade's worth of finances, photos, music, projects, virtual drives, etc...

Can anyone offer any other suggestions or advice? I'm not even sure how recovery software could help? I'm still fairly new to Linux...

Thanks!

Kevin

---

