---
title: "Mounting of CD with AUDIO and DATA on it"
date: 2015-11-01
forum: Hardware
---

### Post by istvan5 on 2015-11-01
Hi !

Following problem, I want to mount a CD, which has AUDIO and a DATA on it. For PC and MAC.

In the file manager, the AUDIO will mount (except that two entries are visible on the file manager),
but the mounting of the DATA part (one entry appear in file manager for this) throws following error:

Error mounting

> Error mounting /dev/sr0 at /media/istvan/Schritte plus 1: Command-line `mount -t "udf" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,umask=0077" "/dev/sr0" "/media/istvan/Schritte plus 1"' exited with non-zero exit status 32: mount: block device /dev/sr0 is write-protected, mounting read-onlymount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

this is what Ubuntu tries

```
mount -t "udf" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,umask=0077" "/dev/sr0" "/media/istvan/Schritte plus 1"
```

-> how  can i mount AUDIO and DATA at once ?

DMESG gives this 
> istvan@Asus:~$ dmesg | tail[  241.475022] Sense Key : Illegal Request [current] 
[  241.475031] sr 4:0:0:0: [sr0]  
[  241.475040] Add. Sense: Illegal mode for this track
[  241.475047] sr 4:0:0:0: [sr0] CDB: 
[  241.475050] Read(10): 28 00 00 00 00 00 00 00 02 00 00 00
[  241.475072] end_request: I/O error, dev sr0, sector 0
[  241.475079] Buffer I/O error on device sr0, logical block 0
[  251.490344] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
[  251.490364] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)
[  285.162939] perf samples too long (2532 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
istvan@Asus:~$ 


VAR/LOG/SYSLOG has this

> Nov  1 12:47:40 Asus kernel: [  226.276190] usb 1-1: new high-speed USB device number 3 using ehci-pciNov  1 12:47:40 Asus kernel: [  226.413192] usb 1-1: New USB device found, idVendor=0e8d, idProduct=1806
Nov  1 12:47:40 Asus kernel: [  226.413209] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov  1 12:47:40 Asus kernel: [  226.413219] usb 1-1: Product: MT1806 
Nov  1 12:47:40 Asus kernel: [  226.413228] usb 1-1: Manufacturer: MediaTek Inc
Nov  1 12:47:40 Asus kernel: [  226.413236] usb 1-1: SerialNumber: R8X76YAD700JTT 
Nov  1 12:47:40 Asus mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1"
Nov  1 12:47:40 Asus mtp-probe: bus: 1, device: 3 was not an MTP device
Nov  1 12:47:40 Asus kernel: [  226.469323] usb-storage 1-1:1.0: USB Mass Storage device detected
Nov  1 12:47:40 Asus kernel: [  226.469634] scsi4 : usb-storage 1-1:1.0
Nov  1 12:47:40 Asus kernel: [  226.469994] usbcore: registered new interface driver usb-storage
Nov  1 12:47:41 Asus kernel: [  227.471237] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SE-208DB  TS01 PQ: 0 ANSI: 0
Nov  1 12:47:41 Asus kernel: [  227.505200] sr0: scsi3-mmc drive: 62x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Nov  1 12:47:41 Asus kernel: [  227.505212] cdrom: Uniform CD-ROM driver Revision: 3.20
Nov  1 12:47:41 Asus kernel: [  227.505696] sr 4:0:0:0: Attached scsi CD-ROM sr0
Nov  1 12:47:41 Asus kernel: [  227.506033] sr 4:0:0:0: Attached scsi generic sg1 type 5
Nov  1 12:47:55 Asus kernel: [  241.470035] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.470046] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  1 12:47:55 Asus kernel: [  241.470053] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.470058] Sense Key : Illegal Request [current] 
Nov  1 12:47:55 Asus kernel: [  241.470068] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.470077] Add. Sense: Illegal mode for this track
Nov  1 12:47:55 Asus kernel: [  241.470084] sr 4:0:0:0: [sr0] CDB: 
Nov  1 12:47:55 Asus kernel: [  241.470089] Read(10): 28 00 00 00 00 00 00 00 02 00 00 00
Nov  1 12:47:55 Asus kernel: [  241.470111] end_request: I/O error, dev sr0, sector 0
Nov  1 12:47:55 Asus kernel: [  241.470120] Buffer I/O error on device sr0, logical block 0
Nov  1 12:47:55 Asus kernel: [  241.472629] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.472639] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  1 12:47:55 Asus kernel: [  241.472646] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.472651] Sense Key : Illegal Request [current] 
Nov  1 12:47:55 Asus kernel: [  241.472660] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.472669] Add. Sense: Illegal mode for this track
Nov  1 12:47:55 Asus kernel: [  241.472676] sr 4:0:0:0: [sr0] CDB: 
Nov  1 12:47:55 Asus kernel: [  241.472681] Read(10): 28 00 00 00 00 00 00 00 02 00 00 00
Nov  1 12:47:55 Asus kernel: [  241.472702] end_request: I/O error, dev sr0, sector 0
Nov  1 12:47:55 Asus kernel: [  241.472712] Buffer I/O error on device sr0, logical block 0
Nov  1 12:47:55 Asus kernel: [  241.475003] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.475011] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov  1 12:47:55 Asus kernel: [  241.475018] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.475022] Sense Key : Illegal Request [current] 
Nov  1 12:47:55 Asus kernel: [  241.475031] sr 4:0:0:0: [sr0]  
Nov  1 12:47:55 Asus kernel: [  241.475040] Add. Sense: Illegal mode for this track
Nov  1 12:47:55 Asus kernel: [  241.475047] sr 4:0:0:0: [sr0] CDB: 
Nov  1 12:47:55 Asus kernel: [  241.475050] Read(10): 28 00 00 00 00 00 00 00 02 00 00 00
Nov  1 12:47:55 Asus kernel: [  241.475072] end_request: I/O error, dev sr0, sector 0
Nov  1 12:47:55 Asus kernel: [  241.475079] Buffer I/O error on device sr0, logical block 0
Nov  1 12:48:05 Asus kernel: [  251.490344] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
Nov  1 12:48:05 Asus kernel: [  251.490364] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)
Nov  1 12:48:39 Asus kernel: [  285.162939] perf samples too long (2532 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Nov  1 12:50:23 Asus kernel: [  389.462118] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
Nov  1 12:50:23 Asus kernel: [  389.462130] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)

in the folder SBIN, I have
mount.ntfs
mount-ntfs-3g

in menu DISKS, I have automatic MOUNT options enabled
it also says here "Content" = UDF not mounted

---

### Post by cyanophyteae on 2015-12-21
Hello! Had the same problem with my HP nc6400 laptop with lubuntu. CD got mounted as audio only despite there being data on the disc.

After doing things I shouldnt be doing and backing up, I ended up with a xubuntu linux install. 15 minutes later, when the CD was inserted Thunar open nicely with data content of the mixed CD. :D
Good luck Brother!

---

