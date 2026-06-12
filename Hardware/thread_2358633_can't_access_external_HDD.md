---
title: "can't access external HDD"
date: 2017-04-15
forum: Hardware
---

### Post by dascheer on 2017-04-15
Hi there!

I am trying to access my external HDD, but I can't seem to find it on my file manager or on gparted. It seems to have a name, "sbd."

The external HDD is a "Seagate Expansion 1TB Portable External Hard Drive USB 3.0 (STEA1000400)."

The operating system is Ubuntu 16.04 and kernal is 4.4.0-72-generic.  

The last bit of print out from dmesg is > [  736.579395] sd 8:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  736.579401] sd 8:0:0:0: [sdb] Sense not available.
[  736.667379] sd 8:0:0:0: [sdb] Write Protect is off
[  736.667385] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  736.707377] sd 8:0:0:0: [sdb] Asking for cache data failed
[  736.707384] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  736.939311] sd 8:0:0:0: [sdb] Read Capacity(16) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  736.939320] sd 8:0:0:0: [sdb] Sense not available.
[  737.059286] sd 8:0:0:0: [sdb] Read Capacity(10) failed: Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[  737.059293] sd 8:0:0:0: [sdb] Sense not available.
[  737.259256] sd 8:0:0:0: [sdb] Attached SCSI disk
[  741.598312] usb 2-1.2: new high-speed USB device number 6 using ehci-pci
[  741.772445] usb 2-1.2: New USB device found, idVendor=0bc2, idProduct=231a
[  741.772451] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  741.772455] usb 2-1.2: Product: Expansion
[  741.772458] usb 2-1.2: Manufacturer: Seagate
[  741.772460] usb 2-1.2: SerialNumber: NA86P45Z
[  741.773401] scsi host9: uas
[  741.775417] scsi 9:0:0:0: Direct-Access     Seagate  Expansion        0707 PQ: 0 ANSI: 6
[  741.777414] sd 9:0:0:0: Attached scsi generic sg2 type 0


Thank you!

---

### Post by yancek on 2017-04-15
Since it shows in your dmesg output, what exactly do you have on it as far as partitions/filesystems and how have you tried to access it?  Partitions on external drives are generally available under the /media/username directory.

---

### Post by dascheer on 2017-04-15
I haven't written anything on it. It's brand new. Thanks for the response.

---

### Post by efflandt on 2017-04-15
You need to partition and format the drive. If you install **gparted** you can do it with that. The live/install system has gparted on it, but it is not installed by default on an installed system.

With that you add a partition table, either **msdos** or **gpt** partition table depending upon what you are going to be doing with the drive. If you ever get a drive larger than 2 TB it would use gpt. Then you add whatever partition(s) you want. Linux typically uses ext4 partitions.

---

### Post by dascheer on 2017-04-16
Thanks for the response. When I'm in gparted, my device, which I believe is called sbd, does not show up in the list of devices.

---

### Post by yancek on 2017-04-16
When you are in GParted you need to click the down arrow in the upper right where the devices are listed to access a second, third, etc. device.  Most likely it will be sdb.

---

