---
title: "Unable to use my external hard drive"
date: 2006-04-15
forum: Hardware &amp; Laptops
---

### Post by daimaku on 2006-04-15
Hello, I have been looking around the web to see if I could help on using my external hard drive (Western Digital 160GB usb) on ubuntu. I tried to do what many forums out there suggested but with no result. The drive is recognized for a couple of seconds. As soon as I plug it into a usb port, I type lsusb in my terminal and this shows up

Bus 004 Device 013: ID 1058:0900 Western Digital Technologies, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

half a minute later when i type the same command again, i get this:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Can some one help me out or point me to a good resource to solve this issue

---

### Post by John.Michael.Kane on 2006-04-15
[http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561](http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561)

---

### Post by daimaku on 2006-04-16
I plug my device in the usb port and i get a output similar to the link:

kernel: Attached scsi disk sda at scsi5, channel 0, id 0, lun 0

when i try to create a filesystem with the command "mkfs.ext3 /dev/sda1" , this happens:

~$ mkfs.ext3 /dev/sda1
mke2fs 1.35 (28-Feb-2004)
mkfs.ext3: No such device or address while trying to determine filesystem size

so when i check /var/log/messages i get this:

Apr 15 20:56:10 localhost kernel: usb 4-1: scsi_eh_5 timed out on ep0in
Apr 15 20:56:10 localhost kernel: scsi: Device offlined - not ready after error recovery: host 5 channel 0 id 0 lun 0
Apr 15 20:56:10 localhost kernel: usb 4-1: USB disconnect, address 30
Apr 15 20:56:11 localhost kernel: usb 4-1: new high speed USB device using ehci_hcd and address 31
Apr 15 20:56:12 localhost kernel: usb 4-1: khubd timed out on ep0in
Apr 15 20:56:17 localhost kernel: usb 4-1: khubd timed out on ep0in
Apr 15 20:56:17 localhost kernel: usb 4-1: new high speed USB device using ehci_hcd and address 32
Apr 15 20:56:18 localhost kernel: usb 4-1: khubd timed out on ep0in
Apr 15 20:56:23 localhost kernel: usb 4-1: khubd timed out on ep0in
Apr 15 20:58:27 localhost gconfd (daimaku-8105): Resolved address "xml:readwrite:/home/daimaku/.gconf" to a writable configuration source at position 0

the device goes offline, how do i keep scsi_eh_5 from getting timed out??

---

