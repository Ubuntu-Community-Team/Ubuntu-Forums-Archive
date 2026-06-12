---
title: "USB flash drive not working (shows up then quickly disappears completely)"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by jnylen on 2008-01-22
As the title says, I have a 512 MB Flash drive that doesn't work in Ubuntu.  It works fine in Windows.  I know it's not the USB port, because I have another thumbdrive that works fine in the same port.

So what happens when I plug it in?  All the normal stuff happens, it automatically mounts, and all the files show up for a second (the device files that appear are /dev/sdb and /dev/sdb1).  Then after a second, everything disappears, including the device files.

Here is the output of a command that should help to diagnose my problem, starting from when I plugged in the drive:

```
james@nylen:~$ tail -fn 0 /var/log/kern.log
Jan 22 14:14:04 nylen kernel: [81920.124000] usb 5-7: new high speed USB device using ehci_hcd and address 53
Jan 22 14:14:04 nylen kernel: [81920.256000] usb 5-7: configuration #1 chosen from 1 choice
Jan 22 14:14:04 nylen kernel: [81920.256000] scsi16 : SCSI emulation for USB Mass Storage devices
Jan 22 14:14:04 nylen kernel: [81920.256000] usb-storage: device found at 53
Jan 22 14:14:04 nylen kernel: [81920.256000] usb-storage: waiting for device to settle before scanning
Jan 22 14:14:09 nylen kernel: [81925.256000] usb-storage: device scan complete
Jan 22 14:14:09 nylen kernel: [81925.272000] scsi 16:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.1  PQ: 0 ANSI: 2
Jan 22 14:14:09 nylen kernel: [81925.276000] sd 16:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
Jan 22 14:14:09 nylen kernel: [81925.276000] sd 16:0:0:0: [sdb] Write Protect is off
Jan 22 14:14:09 nylen kernel: [81925.276000] sd 16:0:0:0: [sdb] Mode Sense: 03 00 00 00
Jan 22 14:14:09 nylen kernel: [81925.276000] sd 16:0:0:0: [sdb] Assuming drive cache: write through
Jan 22 14:14:09 nylen kernel: [81925.280000] sd 16:0:0:0: [sdb] 1000944 512-byte hardware sectors (512 MB)
Jan 22 14:14:09 nylen kernel: [81925.280000] sd 16:0:0:0: [sdb] Write Protect is off
Jan 22 14:14:09 nylen kernel: [81925.280000] sd 16:0:0:0: [sdb] Mode Sense: 03 00 00 00
Jan 22 14:14:09 nylen kernel: [81925.280000] sd 16:0:0:0: [sdb] Assuming drive cache: write through
Jan 22 14:14:09 nylen kernel: [81925.280000]  sdb: sdb1
Jan 22 14:14:09 nylen kernel: [81925.284000] sd 16:0:0:0: [sdb] Attached SCSI removable disk
Jan 22 14:14:09 nylen kernel: [81925.284000] sd 16:0:0:0: Attached scsi generic sg1 type 0
Jan 22 14:14:10 nylen kernel: [81926.548000] usb 5-7: reset high speed USB device using ehci_hcd and address 53
Jan 22 14:14:10 nylen kernel: [81926.800000] usb 5-7: reset high speed USB device using ehci_hcd and address 53
Jan 22 14:14:11 nylen kernel: [81927.068000] usb 5-7: reset high speed USB device using ehci_hcd and address 53
Jan 22 14:14:11 nylen kernel: [81927.180000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:11 nylen kernel: [81927.396000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:11 nylen kernel: [81927.612000] usb 5-7: reset high speed USB device using ehci_hcd and address 53
Jan 22 14:14:11 nylen kernel: [81927.724000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:12 nylen kernel: [81927.940000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:12 nylen kernel: [81928.156000] usb 5-7: reset high speed USB device using ehci_hcd and address 53
Jan 22 14:14:12 nylen kernel: [81928.564000] usb 5-7: device not accepting address 53, error -71
Jan 22 14:14:12 nylen kernel: [81928.676000] usb 5-7: reset high speed USB device using ehci_hcd and address 53
Jan 22 14:14:13 nylen kernel: [81929.084000] usb 5-7: device not accepting address 53, error -71
Jan 22 14:14:13 nylen kernel: [81929.084000] usb 5-7: USB disconnect, address 53
Jan 22 14:14:13 nylen kernel: [81929.088000] scsi 16:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 22 14:14:13 nylen kernel: [81929.088000] end_request: I/O error, dev sdb, sector 280
Jan 22 14:14:13 nylen kernel: [81929.124000] FAT: FAT read failed (blocknr 47)
Jan 22 14:14:13 nylen kernel: [81929.124000] scsi 16:0:0:0: rejecting I/O to dead device
Jan 22 14:14:13 nylen kernel: [81929.124000] FAT: FAT read failed (blocknr 34)
Jan 22 14:14:13 nylen kernel: [81929.132000] scsi 16:0:0:0: rejecting I/O to dead device
Jan 22 14:14:13 nylen kernel: [81929.132000] FAT: FAT read failed (blocknr 34)
Jan 22 14:14:13 nylen kernel: [81929.144000] scsi 16:0:0:0: rejecting I/O to dead device
Jan 22 14:14:13 nylen last message repeated 3 times
Jan 22 14:14:13 nylen kernel: [81929.144000] scsi 16:0:0:0: [sdb] READ CAPACITY failed
Jan 22 14:14:13 nylen kernel: [81929.144000] scsi 16:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Jan 22 14:14:13 nylen kernel: [81929.144000] scsi 16:0:0:0: [sdb] Sense not available.
Jan 22 14:14:13 nylen kernel: [81929.148000] scsi 16:0:0:0: rejecting I/O to dead device
Jan 22 14:14:13 nylen kernel: [81929.148000] scsi 16:0:0:0: [sdb] Write Protect is off
Jan 22 14:14:13 nylen kernel: [81929.148000] scsi 16:0:0:0: [sdb] Mode Sense: 00 00 00 00
Jan 22 14:14:13 nylen kernel: [81929.148000] scsi 16:0:0:0: [sdb] Assuming drive cache: write through
Jan 22 14:14:13 nylen kernel: [81929.196000] usb 5-7: new high speed USB device using ehci_hcd and address 54
Jan 22 14:14:13 nylen kernel: [81929.308000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:13 nylen kernel: [81929.524000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:13 nylen kernel: [81929.740000] usb 5-7: new high speed USB device using ehci_hcd and address 55
Jan 22 14:14:13 nylen kernel: [81929.852000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:14 nylen kernel: [81930.068000] usb 5-7: device descriptor read/64, error -71
Jan 22 14:14:14 nylen kernel: [81930.284000] usb 5-7: new high speed USB device using ehci_hcd and address 56
Jan 22 14:14:14 nylen kernel: [81930.692000] usb 5-7: device not accepting address 56, error -71
Jan 22 14:14:14 nylen kernel: [81930.804000] usb 5-7: new high speed USB device using ehci_hcd and address 57
Jan 22 14:14:15 nylen kernel: [81931.212000] usb 5-7: device not accepting address 57, error -71

```

If anybody here can help me, thanks in advance.

---

### Post by eggdeng on 2008-01-22
Try mounting manually.
```
sudo mkdir /media/thumbdrive
```
```
sudo mount /dev/sdb1 /media/thumbdrive
```

---

### Post by Daelyn on 2008-01-24
If above is not working, what about you trying USB1 mode just for the sake of testing and seeing what happens.

```
 sudo rmmod ehci_hcd 
```

This will remove module "ehci_hcd" from your currently running session and attempt to use all devices in USB1.1 mode. Upon reboot, it will be used again.

```
 sudo modprobe ehci_hcd 
```
will put the module in use again, in your currently running session.

it is possible to have the module blacklisted so it will not load again, but, unfortunately I've forgotten the location of that file. Can be found just about anywhere if you search for "blacklist module". 

Tell us what happens and we'll investigate further.

---

### Post by Nephiel on 2008-01-24
I have the same problem. I am sure that it's not the port, as it happens in the ports of my motherboard (VIA chipset) and in the ports of two different PCI cards with Ali and NEC chipsets.

I've googled it and I believe it may be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746).

Unloading ehci_hcd to work in USB 1.1 mode is not a practical solution because USB 1.1 is way too slow for file transfer.

Any ideas?

---

### Post by Daelyn on 2008-01-25
> **Nephiel said:**
> I have the same problem. I am sure that it's not the port, as it happens in the ports of my motherboard (VIA chipset) and in the ports of two different PCI cards with Ali and NEC chipsets.

I've googled it and I believe it may be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746).

Unloading ehci_hcd to work in USB 1.1 mode is not a practical solution because USB 1.1 is way too slow for file transfer.

Any ideas?

I know that unloading the module to force USB 1.1 mode makes it slow, but, the question was if it works afterwards or not.

I found quite some information about people having trhe same issue, and well, it works unloading the module. Someone mentioned HW fault, but I do not know.

Are you guys using a USB hub by any chance?

---

### Post by Nephiel on 2008-01-27
No hub, I'm using the USB ports that are directly on the motherboard, on the rear of the computer. And this also happens with three different PCI USB adapters.

I made a few tests in the same computer, same drives, same USB port, same 2GB file being transferred (from IDE EXT3 hard drive to USB FAT drive). I ran a fsck -a on the USB drive between tests.
-Booted with Windows: USB transfers worked at USB 2.0 speed.
-Booted with Ubuntu 5.10 (Breezy) from a LiveCD: USB transfers worked at USB 2.0 speed.
-Booted with Ubuntu 6.06 LTS (Dapper) installed: USB reset problem is present.
-Booted with Ubuntu 7.10 (Gutsy) from a LiveCD: USB reset problem is present.

Since it works with Windows and Breezy, it doesn't look like HW fault.
The oldest kernel I've tried where this problem is present is 2.6.15-23. The latest is 2.6.22-14-generic.
So I'm guessing at some point between Breezy and Dapper a change was made in the kernel and/or the USB modules that introduced this problem.

And yes, removing the module works; but it's too slow, so using it for backups and synching is out of the question.

---

