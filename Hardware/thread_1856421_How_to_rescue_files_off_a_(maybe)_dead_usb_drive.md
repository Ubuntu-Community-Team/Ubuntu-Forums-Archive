---
title: "How to rescue files off a (maybe) dead usb drive?"
date: 2011-10-08
forum: Hardware
---

### Post by captain.sunset on 2011-10-08
Hi,

I have a laptop that lost power which affected an attached usb drive (ntfs formatted). The drive no longer mounts automatically :( and the device that it belongs to is only accessible for about a few seconds at most. Although I don't care about the drive itself I would like to recover the data on it. Is there a way that I can either bring the drive online or somehow get access to the data? I have tried to dd/dd_rescue the device (/dev/sdc) but the device isnt online enough for the data to be accessed. Thanks.

Harold.

A copy of the kern.log is shown:

  kernel: [ 5763.236263] ses 90:0:0:1: Attached scsi generic sg3 type 13
  kernel: [ 5919.980633] sd 93:0:0:0: [sdb] No Caching mode page present
  kernel: [ 5919.980641] sd 93:0:0:0: [sdb] Assuming drive cache: write through
  kernel: [ 5943.668078] usb 1-4: device descriptor read/64, error -110
  kernel: [ 5958.884080] usb 1-4: device descriptor read/64, error -110
  kernel: [ 5959.100083] usb 1-4: reset high speed USB device using ehci_hcd and   address 94
  kernel: [ 5959.236300] sd 93:0:0:0: Device offlined - not ready after error recovery
  kernel: [ 5959.236320] sd 93:0:0:0: [sdb] Unhandled error code
  kernel: [ 5959.236325] sd 93:0:0:0: [sdb]  
  kernel: [ 5959.236332] usb 1-4: USB disconnect, address 94
  kernel: [ 5959.236339] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
  kernel: [ 5959.236344] sd 93:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
  kernel: [ 5959.236366] end_request: I/O error, dev sdb, sector 0
  kernel: [ 5959.236374] Buffer I/O error on device sdb, logical block 0
  kernel: [ 5959.236407] sd 93:0:0:0: rejecting I/O to offline device

---

### Post by sanderd17 on 2011-10-08
How many hard disks do you have on that computer?

Can you plug in the USB stick and execute 
```

ls /dev/sd*

```

and 
```

lsusb

```

---

### Post by captain.sunset on 2011-10-08
On internal drive (it shows up as /dev/sda).

/var/log# ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb

/var/log# lsusb
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Harold.

---

### Post by sanderd17 on 2011-10-08
And what do you see when you execute

```

mkdir /media/myusb
mount /dev/sdb /media/myusb

```

---

### Post by captain.sunset on 2011-10-08
# mount /dev/sdb /media/myusb
mount: Resource temporarily unavailable

---

### Post by sanderd17 on 2011-10-08
Sorry, I overlooked it.

You disk seems to have lost it's partitions, only the disk itself remains. Off coarse you can't mount that.

Repartitioning should help make your USB usable again, but saving your data will be very difficult. 

Maybe one of this tools will help: [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Not that you need a live CD, but the tools stay the same.

---

### Post by captain.sunset on 2011-10-08
Thanks for the response. I shall look and see if any of these tools help.

Harold.

---

