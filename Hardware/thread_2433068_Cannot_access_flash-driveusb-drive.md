---
title: "Cannot access flash-drive/usb-drive"
date: 2019-12-13
forum: Hardware
---

### Post by aalemann on 2019-12-13
My USB flash drive is no longer working after using it at one of this self-service-photo-print-machines. The software on that machine crashed when I was scrolling through my photos on my flash drive and just wanted to change the viewing order of the files. I was not able to read anything from the flash drive after that crash.

Inserting the drive on my [FONT=courier new]Ubuntu 18.04.3 LTS[/FONT] and looking into the [FONT=courier new]/var/log/syslog[/FONT], I see the following (related) error messages:

```

    kernel: [2661765.200803] usb-storage 4-1:1.0: USB Mass Storage device detected
    kernel: [2661765.201724] scsi host6: usb-storage 4-1:1.0
    mtp-probe: checking bus 4, device 9: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-1"
    mtp-probe: bus: 4, device: 9 was not an MTP device
    upowerd[2591]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0
    upowerd[2591]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb4/4-1
    org.xfce.FileManager[2344]: thunar-volman: Unsupported USB device type "usb".
    org.xfce.FileManager[2344]: thunar-volman: Unsupported USB device type "usb-storage".
    kernel: [2661766.632180] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 64GB   1100 PQ: 0 ANSI: 6
    kernel: [2661766.632813] sd 6:0:0:0: Attached scsi generic sg2 type 0
    kernel: [2661766.634459] sd 6:0:0:0: [sdb] 123404288 512-byte logical blocks: (63.2 GB/58.8 GiB)
    kernel: [2661766.635203] sd 6:0:0:0: [sdb] Write Protect is off
    kernel: [2661766.635205] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
    kernel: [2661766.636058] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
    kernel: [2661766.640941] scsi_io_completion: 4 callbacks suppressed
    kernel: [2661766.640944] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
    kernel: [2661766.640947] sd 6:0:0:0: [sdb] tag#0 Sense Key : Not Ready [current] 
    kernel: [2661766.640949] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Medium not present
    kernel: [2661766.640952] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
    kernel: [2661766.640953] print_req_error: 4 callbacks suppressed

```

The flash drive seems to be recognized, although the size is wrong, it has 128 GB.

After those messages, however, the [FONT=courier new]Buffer I/O[/FONT] error appears:

```

    kernel: [2661766.640954] print_req_error: I/O error, dev sdb, sector 0
    kernel: [2661766.640957] buffer_io_error: 3 callbacks suppressed
    kernel: [2661766.640958] Buffer I/O error on dev sdb, logical block 0, async page read
    kernel: [2661766.641870] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
    kernel: [2661766.641873] sd 6:0:0:0: [sdb] tag#0 Sense Key : Not Ready [current] 
    kernel: [2661766.641875] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Medium not present
    kernel: [2661766.641877] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00

```

The following part is repeated 8 times:

```

    kernel: [2661766.641878] print_req_error: I/O error, dev sdb, sector 0
    kernel: [2661766.641881] Buffer I/O error on dev sdb, logical block 0, async page read
    kernel: [2661766.642774] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
    kernel: [2661766.642776] sd 6:0:0:0: [sdb] tag#0 Sense Key : Not Ready [current] 
    kernel: [2661766.642777] sd 6:0:0:0: [sdb] tag#0 Add. Sense: Medium not present
    kernel: [2661766.642778] sd 6:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00

```

The final part is as follows:

```

    kernel: [2661766.649002] print_req_error: I/O error, dev sdb, sector 24
    kernel: [2661766.649004] Buffer I/O error on dev sdb, logical block 3, async page read
    kernel: [2661766.650832]  sdb: unable to read partition table
    kernel: [2661766.653438] sd 6:0:0:0: [sdb] Attached SCSI removable disk
    org.xfce.FileManager[2344]: thunar-volman: Unknown block device type "disk".
    colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1

```

I am worried about the *[FONT=courier new]unable to read partition table[/FONT]* part, but that might be related to the *[FONT=courier new]Buffer I/O[/FONT]* message.

I have no idea how to restore my flash drive, as **[FONT=courier new]# smartctl -a /dev/sdb[/FONT]** results only in 

```

    /dev/sdb: Unknown USB bridge [0x8564:0x1000 (0x1100)]
    Please specify device type with the -d option.

```

Manually setting the type with **[FONT=courier new]# smartctl -d scsi -a /dev/sdb[/FONT]** gives the following output (local time and serial number removed as they should not be important)

```

    === START OF INFORMATION SECTION ===
    Vendor:               JetFlash
    Product:              Transcend 64GB
    Revision:             1100
    Compliance:           SPC-4
    User Capacity:        63.182.995.456 bytes [63,1 GB]
    Logical block size:   512 bytes
    LU is fully provisioned
    scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
    Logical Unit id:      0x00010200000608040x2020030102060804error: SCSI name string
    Device type:          disk
    scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
    SMART support is:     Available - device has SMART capability.
    SMART support is:     Disabled
    Temperature Warning:  Disabled or Not Supported

    === START OF READ SMART DATA SECTION ===
    SMART Health Status: OK
    Current Drive Temperature:     0 C
    Drive Trip Temperature:        0 C

    Error Counter logging not supported

    scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
    Device does not support Self Test logging

```

Again, wrong size. 

Any suggestions how I could try to get access to my flash-drive are greatly appreciated!

---

### Post by ajgreeny on 2019-12-13
There is no indication (or I missed it in the output you posted) but a 128G USB flash drive would normally be formatted to exFat at time of purchase.

Have you reformatted it to any other filesystem?  If it's now NTFS it may simply need chkdsk run on it from a Windows machine as following a crash and unsafe shutdown of the flash drive it may appear still in use when inserted in your Ubuntu machine.

---

### Post by aalemann on 2019-12-13
> **ajgreeny said:**
> There is no indication (or I missed it in the output you posted) but a 128G USB flash drive would normally be formatted to exFat at time of purchase.

Have you reformatted it to any other filesystem?  If it's now NTFS it may simply need chkdsk run on it from a Windows machine as following a crash and unsafe shutdown of the flash drive it may appear still in use when inserted in your Ubuntu machine.

Thanks for your answer! I have not reformatted it, so I guess it is exFat then. When I connect the flash drive to a windows machine, it keeps asking me if I want to format it. The photo-machine crashed when my flash drive was still in use, so this might be the reason for my problems. So I will try to somehow run chkdsk on a different windows machine and see if that helps.

---

### Post by aalemann on 2019-12-13
> **ajgreeny said:**
> If it's now NTFS it may simply need chkdsk run on it from a Windows machine as following a crash and unsafe shutdown of the flash drive it may appear still in use when inserted in your Ubuntu machine.

I just tried chkdsk, but it is not working, it basically says *CHKDSK is not available for RAW*

---

### Post by ajgreeny on 2019-12-13
It sounds as if the partition table has been corrupted, so I am not sure where best to go from here but I believe Testdisk may be of use to restore the partitions.

I have never used Testdisk so I offer this only as a possible answer, having read about it here and elsewhere, and will have to leave you to investigate further.

See [https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk) for all details.

---

### Post by aalemann on 2019-12-13
> **ajgreeny said:**
> It sounds as if the partition table has been corrupted, so I am not sure where best to go from here but I believe Testdisk may be of use to restore the partitions.

I have never used Testdisk so I offer this only as a possible answer, having read about it here and elsewhere, and will have to leave you to investigate further.

See [https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk) for all details.

Indeed, will explore Testdisk later today, thanks

---

