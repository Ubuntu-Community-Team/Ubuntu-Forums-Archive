---
title: "IDE-&gt;USB 2.0 adapter doesn't expose DVD drive properly"
date: 2008-07-24
forum: Hardware
---

### Post by oddhack on 2008-07-24
I'm running stock hardy 2.6.24-19-generic on a Gigabyte GA-MA78GM-S2H + Athlon X2 5000 system, using Xubuntu (running with gdm disabled and starting my session with Window Maker - so there's no Gnome desktop software stack or anything of that nature, this is all being done at the command line), using an external IDE->USB 2 adapter.

The adapter works OK for IDE hard drives, but something funky is happening with my DVD drive - the device shows up **twice** in /dev, but neither device is mountable. lsusb on the adapter shows:

> 
% lsusb
Bus 002 Device 008: ID 04cf:8818 Myson Century, Inc. USB2.0 to ATAPI Bridge Controller


When I try to attach an NEC ND-3540A DVD drive using the adapter, syslog shows:

> 
Jul 24 11:33:34 brad kernel: [15566.346754] usb 2-6: new high speed USB device using ehci_hcd and address 8
Jul 24 11:33:34 brad kernel: [15566.398063] usb 2-6: configuration #1 chosen from 1 choice
Jul 24 11:33:34 brad NetworkManager: <debug> [1216924414.287163] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100').
Jul 24 11:33:34 brad kernel: [15566.402440] scsi12 : SCSI emulation for USB Mass Storage devices
Jul 24 11:33:34 brad kernel: [15566.404812] usb-storage: device found at 8
Jul 24 11:33:34 brad kernel: [15566.404815] usb-storage: waiting for device to settle before scanning
Jul 24 11:33:34 brad NetworkManager: <debug> [1216924414.421947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100_if0').
Jul 24 11:33:39 brad kernel: [15568.319940] usb-storage: device scan complete
Jul 24 11:33:39 brad kernel: [15568.322649] scsi 12:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0 CCS
Jul 24 11:33:39 brad kernel: [15568.322843] scsi 12:0:0:1: Direct-Access                                    PQ: 0 ANSI: 0 CCS
Jul 24 11:33:39 brad kernel: [15568.323939] sd 12:0:0:0: [sdb] 6815848 512-byte hardware sectors (3490 MB)
Jul 24 11:33:39 brad kernel: [15568.324258] sd 12:0:0:0: [sdb] Write Protect is off
Jul 24 11:33:39 brad kernel: [15568.324263] sd 12:0:0:0: [sdb] Mode Sense: 00 14 00 00
Jul 24 11:33:39 brad kernel: [15568.324265] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jul 24 11:33:39 brad kernel: [15568.324996] sd 12:0:0:0: [sdb] 6815848 512-byte hardware sectors (3490 MB)
Jul 24 11:33:39 brad kernel: [15568.325664] sd 12:0:0:0: [sdb] Write Protect is off
Jul 24 11:33:39 brad kernel: [15568.325668] sd 12:0:0:0: [sdb] Mode Sense: 00 14 00 00
Jul 24 11:33:39 brad kernel: [15568.325671] sd 12:0:0:0: [sdb] Assuming drive cache: write through
Jul 24 11:33:39 brad kernel: [15568.325676]  sdb: unknown partition table
Jul 24 11:33:39 brad kernel: [15568.327443] sd 12:0:0:0: [sdb] Attached SCSI disk
Jul 24 11:33:39 brad kernel: [15568.327473] sd 12:0:0:0: Attached scsi generic sg1 type 0
Jul 24 11:33:39 brad kernel: [15568.328209] sd 12:0:0:1: [sdc] 6815848 512-byte hardware sectors (3490 MB)
Jul 24 11:33:39 brad kernel: [15568.328885] sd 12:0:0:1: [sdc] Write Protect is off
Jul 24 11:33:39 brad kernel: [15568.328891] sd 12:0:0:1: [sdc] Mode Sense: 00 14 00 00
Jul 24 11:33:39 brad kernel: [15568.328893] sd 12:0:0:1: [sdc] Assuming drive cache: write through
Jul 24 11:33:39 brad kernel: [15568.329978] sd 12:0:0:1: [sdc] 6815848 512-byte hardware sectors (3490 MB)
Jul 24 11:33:39 brad kernel: [15568.330651] sd 12:0:0:1: [sdc] Write Protect is off
Jul 24 11:33:39 brad kernel: [15568.330654] sd 12:0:0:1: [sdc] Mode Sense: 00 14 00 00
Jul 24 11:33:39 brad kernel: [15568.330658] sd 12:0:0:1: [sdc] Assuming drive cache: write through
Jul 24 11:33:39 brad kernel: [15568.330661]  sdc: unknown partition table
Jul 24 11:33:39 brad kernel: [15568.332565] sd 12:0:0:1: [sdc] Attached SCSI disk
Jul 24 11:33:39 brad kernel: [15568.332597] sd 12:0:0:1: Attached scsi generic sg2 type 0
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.417781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100_scsi_host').
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.426041] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100_scsi_host_scsi_device_lun0').
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.427671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100_scsi_host_scsi_device_lun1').
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.436507] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100_scsi_host_scsi_device_lun0_scsi_generic').
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.449406] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4cf_8818_100_scsi_host_scsi_device_lun1_scsi_generic').
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.607573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Myson_Century__Inc__USB_Mass_Storage_Device_100').
Jul 24 11:33:39 brad NetworkManager: <debug> [1216924419.643758] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Myson_Century__Inc__USB_Mass_Storage_Device_100_0').


However, I can't mount a DVD:

> 
% mount -t iso9660 /dev/sdb /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Syslog shows:

> 
Jul 24 11:34:10 brad kernel: [15580.391038] ISOFS: Unable to identify CD-ROM format.


The same error comes from mounting as '-t udf', and syslog in this case
shows:

> 
Jul 24 11:34:16 brad kernel: [15582.752595] UDF-fs: No partition found (1)


The same errors occur when mounting /dev/sdc instead of /dev/sdb, as well.

I can 'dd' off the device without errors, but what I always get, whether
there's a CD or DVD in the drive, is a 3.5GB blob that isn't recognized
as either a UDF or ISO9660 filesystem when I try to loop-mount it.

Finally, lsscsi doesn't appear to recognize the drive, although it acknowledges its existence:

> 
% lsscsi
[2:0:0:0]    disk    ATA      SAMSUNG HD753LJ  1AA0  /dev/sda
[12:0:0:0]   disk                                    /dev/sdb
[12:0:0:1]   disk                                    /dev/sdc


This is all completely repeatable. Any thoughts on how to get the drive to work?

It's not out of the question this is a problem with the motherboard - the reason I'm trying the USB adapter is that I get multitudinous errors when plugging the drive directly into the motherboard IDE channel, ending up falling back to UDMA/25 mode and taking many minutes to boot. It is unlikely to be a problem with the drive, however, as it works perfectly on my old Abit NF7-S motherboard under gutsy.

---

