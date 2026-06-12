---
title: "USB hard drive not recognised after upgrading to 11.04?"
date: 2011-06-12
forum: Hardware
---

### Post by jjepUser86 on 2011-06-12
My Buffalo USB 250GB hard drive doesn't seem to be recognised after I upgraded Ubuntu to version 11.04...

Any ideas how to fix this problem?...

USB 1GB stick does work, but if I plug the USB hard drive nothing seems to happen...It does work though on Windows XP...?!

thnx for any help :p

---

### Post by trozamon on 2011-06-12
Plug in the hard drive, then run this in a terminal and post the results:

```
lsusb
```

---

### Post by jjepUser86 on 2011-06-13
> **trozamon said:**
> Plug in the hard drive, then run this in a terminal and post the results:

```
lsusb
```


Here is the result before I plugged the hard drive: 

Bus 002 Device 002: ID 045e:071d Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and when I plugged the hard drive and tried again the prompt just keeps blinking the square...?!..It doesn't return any output to terminal...

also I tried to insert 1GB USB stick when the hard drive was plugged...the system didn't respond to the stick?!...and when I plugged the hard drive out, immediately the USB stick was recognized...?!

The hard drive worked just fine before the update....and does work in XP...

---

### Post by trozamon on 2011-06-14
Plug in the hard drive, then run:

```
dmesg | tail -n 100
```

Post the output here.

P.S. Also, when you post output from the terminal, could you put it in code tags to make it easier to see please? Thank you.

---

### Post by jjepUser86 on 2011-06-15
> **trozamon said:**
> Plug in the hard drive, then run:

```
dmesg | tail -n 100
```Post the output here.

P.S. Also, when you post output from the terminal, could you put it in code tags to make it easier to see please? Thank you.

I'm sorry I got inpatient for fixing the problem and installed 10.10 back =) so no need for help anymore, thank you anyway for answering! =)

here are my findings I still want to share: 

I googled the problem and found out many other people had the same problem. I noticed most of these users had the same BUFFALO USB hard drive as I did. Here's the site with people with the same problem (It's in finnish though so I don't know if it'll help...) :

[http://forum.ubuntu-fi.org/index.php?action=printpage;topic=38801.0](http://forum.ubuntu-fi.org/index.php?action=printpage;topic=38801.0)

Anyway one guy thought that the external hard drive's file system(FAT32) might get converted from ext4 --> swap. He suspected GRUB might do this, because it thinks the USB hard drive is /dev/sda. One guy had no problems, but he said he had external hard drive unplugged?!

hope this helps someone x)

---

### Post by jjepUser86 on 2011-06-29
Hi again! I installed again 11.04 hoping the Buffalo drive would work now...

still no luck...If anyone wants to try and help here's the output:
of the "dmesg | tail -n 30" command after plugging the Buffalo drive:


```

 [117872.901323] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[117872.929312] sd 21:0:0:0: [sdb] Test WP failed, assume Write Enabled
[117872.946331] sd 21:0:0:0: [sdb] Asking for cache data failed
[117872.946344] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[117877.103151] usb 2-1: USB disconnect, address 11
[117877.103752] sd 21:0:0:0: [sdb] Unhandled error code
[117877.103759] sd 21:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[117877.103769] sd 21:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[117877.103788] end_request: I/O error, dev sdb, sector 0
[117877.103796] Buffer I/O error on device sdb, logical block 0
[117877.104533] ldm_validate_partition_table(): Disk read failed.
[117877.104730] Dev sdb: unable to read RDB block 0
[117877.104858]  sdb: unable to read partition table
[117877.106526] sd 21:0:0:0: [sdb] READ CAPACITY failed
[117877.106535] sd 21:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[117877.106544] sd 21:0:0:0: [sdb] Sense not available.
[117877.106586] sd 21:0:0:0: [sdb] Asking for cache data failed
[117877.106591] sd 21:0:0:0: [sdb] Assuming drive cache: write through
[117877.106598] sd 21:0:0:0: [sdb] Attached SCSI disk
[117906.824050] usb 1-2: new high speed USB device using ehci_hcd and address 29
[117907.032438] scsi22 : usb-storage 1-2:1.0
[117917.509877] scsi 22:0:0:0: Direct-Access     USB-HS   WDC WD2500BB-22G 0.01 PQ: 0 ANSI: 0
[117917.510261] sd 22:0:0:0: Attached scsi generic sg1 type 0
[117917.512491] sd 22:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[117917.514110] sd 22:0:0:0: [sdb] Write Protect is off
[117917.514114] sd 22:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[117917.628046] usb 1-2: reset high speed USB device using ehci_hcd and address 29
[117932.740040] usb 1-2: device descriptor read/64, error -110
[117947.956035] usb 1-2: device descriptor read/64, error -110
[117948.172056] usb 1-2: reset high speed USB device using ehci_hcd and address 29

```

all help appreciated :)

---

