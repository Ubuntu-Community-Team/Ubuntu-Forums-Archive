---
title: "USB 2.0 external HD enclosure drive stopped automounting ..."
date: 2009-11-09
forum: Hardware
---

### Post by Morales2k on 2009-11-09
Hi, I need to get to the bottom of this and I will appreciate any help I can get.  

This drive holds all my important media, and now I cant use it so I am a bit panicked right now... 

anyhow...  I searched around and none of the other threads seems to solve my issue so here I am posting a new one.  

So here I go with what Ive seen others do: 
 dmesg | tail gave me the following: 
```
[ 1993.784208] usb 1-4: configuration #1 chosen from 1 choice
[ 1993.886835] Initializing USB Mass Storage driver...
[ 1993.887746] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1993.887987] usbcore: registered new interface driver usb-storage
[ 1993.887996] USB Mass Storage support registered.
[ 1993.888419] usb-storage: device found at 4
[ 1993.888423] usb-storage: waiting for device to settle before scanning
[ 1998.882895] usb-storage: device scan complete
[ 2005.010104] usb 1-4: reset high speed USB device using ehci_hcd and address 4
[ 2005.164116] scsi 2:0:0:0: Device offlined - not ready after error recovery

```blkid does not show a path to my drive on the file... I am thinking that the command gets the info from the fstab or mtab files...!? The thing is that its not showing my drive... :(

df -k returns the following:```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             68089944  19607396  45023760  31% /
udev                   1964188       288   1963900   1% /dev
none                   1964188       516   1963672   1% /dev/shm
none                   1964188       124   1964064   1% /var/run
none                   1964188         0   1964188   0% /var/lock
none                   1964188         0   1964188   0% /lib/init/rw
```i am not sure if there are other commands I can run to help me diagnose this... I know I have tried to use other mounting options but so far I havent come to something that can see or detect that the drive is plugged in and turned on... (Curses!)

Any help will be insanely appreciated!

EDIT:

I got a different enclosure from a friend, and I ran the commands above once more... here is dmesg | tail output:
```
[ 9137.282577] usb 1-4: USB disconnect, address 5
[10003.012626] usb 1-4: new high speed USB device using ehci_hcd and address 6
[10003.164994] usb 1-4: configuration #1 chosen from 1 choice
[10003.173910] scsi4 : SCSI emulation for USB Mass Storage devices
[10003.174282] usb-storage: device found at 6
[10003.174288] usb-storage: waiting for device to settle before scanning
[10008.170564] usb-storage: device scan complete
[10008.171456] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[10008.172498] sd 4:0:0:0: Attached scsi generic sg2 type 0
[10008.184848] sd 4:0:0:0: [sdb] Attached SCSI disk

```Here's df -k output (stayed the same!?):
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             68089944  19609980  45021176  31% /
udev                   1964188       292   1963896   1% /dev
none                   1964188       572   1963616   1% /dev/shm
none                   1964188       124   1964064   1% /var/run
none                   1964188         0   1964188   0% /var/lock
none                   1964188         0   1964188   0% /lib/init/rw
```Maybe the drive is corrupted??? How can I find out!?

Please help!

Wow... still no help... do I need to bring forth some more information!? Isn't that enough!?

---

