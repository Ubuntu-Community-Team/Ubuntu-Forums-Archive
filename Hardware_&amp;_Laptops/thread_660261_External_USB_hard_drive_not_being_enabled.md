---
title: "External USB hard drive not being enabled"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by Alex135 on 2008-01-06
Im running Ubuntu 7.10 64bit with KDE and Gnome installed.

I created a back up Hard drive to store my important files in before i rebuilt my Ubuntu system (gnome stopped working) and now i try and set it back up and its not working.
I know i could mount it from the internal slot, but i want to make this thing work on external because this not working could lead to other problems.
I had done some reading and i did *sudo modprobe -r ehci_hcd* and it executed, but it never fixed my problem. I need to make things work with the 2.0 USB drivers enabled.

Anyone have any ideas on how to fix this?

Thanks in advance.

---

### Post by taurus on 2008-01-06
Can you mount it by hand from a terminal?  What filesystem is it?  Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Alex135 on 2008-01-06
No i cant mount it by hand, the drive would show up as /dev/sdb but there is no such file.

It is standard Ubuntu file system.

i ran *sudo fdisk -l* and all i see is my standard Ubuntu partitions on my internal drive.

```
alex@localhost:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a4dff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

```


Btw, my first post was slightly inaccurate, i ran *modprobe -r ehci_hcd* once and it worked, but it never worked again later. And from what i know that sets the USB port into 1.0 and not 2.0 like i need.

---

### Post by taurus on 2008-01-06
Did you create a partition and format it?  It should look something like /dev/sdb1.  If it says /dev/sdb, it means you have not created a partition and format it.

---

### Post by Yellow Pasque on 2008-01-06
When you plug the drive in, does lsusb see it?

---

### Post by Alex135 on 2008-01-07
there is nothing there, and yes i did do that, however i think i have figured out the problem.

I think my HDD is failing, I have tons of errors, ill try and reinstall Ubuntu on another hdd and edit this post with results.

[edit:] its still not fixed, however i was right, my internal HDD was failing, so allot of my errors were from that, but my problem is still not fixed.

---

### Post by Alex135 on 2008-01-08
Sorry, but i need help...
BUMP!

---

### Post by Daelyn on 2008-01-09
All right, think we're running around wrong here mate.

Do the following.

Reboot machine with Live CD inserted.
Once laoded into gnome desktop I want you to plug in the external HDD, open terminal and post output of these.

```
dmesg
```
Post the last twenty lines of that one, not needed with all the output.
```
lsusb
```
```
sudo fdisk -l
```

This will check if the HDD is identified and also if it has any partitions or not and we'll take it from there.

---

### Post by Alex135 on 2008-01-09
ok that is strange, i poped the disk in, and everything in working in the live cd, but not in the installation.


for *dmesg*:
```
[ 1029.095134] usb 2-6: new high speed USB device using ehci_hcd and address 3
[ 1029.229547] usb 2-6: configuration #1 chosen from 1 choice
[ 1029.579904] usbcore: registered new interface driver libusual
[ 1029.655353] Initializing USB Mass Storage driver...
[ 1029.655409] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1029.655452] usb-storage: device found at 3
[ 1029.655455] usb-storage: waiting for device to settle before scanning
[ 1029.655467] usbcore: registered new interface driver usb-storage
[ 1029.655470] USB Mass Storage support registered.
[ 1034.654506] usb-storage: device scan complete
[ 1034.655377] scsi 8:0:0:0: Direct-Access     USB 2.0  Storage Device   0111 PQ: 0 ANSI: 0 CCS
[ 1037.484871] sd 8:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16).
[ 1037.485212] sd 8:0:0:0: [sda] READ CAPACITY(16) failed
[ 1037.485215] sd 8:0:0:0: [sda] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 1037.485218] sd 8:0:0:0: [sda] Use 0xffffffff as device size
[ 1037.485221] sd 8:0:0:0: [sda] 4294967296 512-byte hardware sectors (2199023 MB)
[ 1037.487476] sd 8:0:0:0: [sda] Write Protect is off
[ 1037.487478] sd 8:0:0:0: [sda] Mode Sense: 08 00 00 00
[ 1037.487480] sd 8:0:0:0: [sda] Assuming drive cache: write through
[ 1037.489850] sd 8:0:0:0: [sda] 4294967295 512-byte hardware sectors (2199023 MB)
[ 1037.491474] sd 8:0:0:0: [sda] Write Protect is off
[ 1037.491477] sd 8:0:0:0: [sda] Mode Sense: 08 00 00 00
[ 1037.491479] sd 8:0:0:0: [sda] Assuming drive cache: write through
[ 1037.491482]  sda: sda1
[ 1037.506425] sd 8:0:0:0: [sda] Attached SCSI disk
[ 1037.546985] sd 8:0:0:0: Attached scsi generic sg0 type 0
[ 1039.513699] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1039.513706] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1041.437431] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1041.437434] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1043.361168] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1043.361171] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1045.294909] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1045.294915] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1047.218648] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1047.218654] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1049.142379] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1049.142382] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1051.066121] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1051.066127] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1052.989853] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1052.989856] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1054.913591] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1054.913596] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1056.837328] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1056.837332] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1058.761071] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1058.761078] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1060.684807] sd 8:0:0:0: [sda] Sense Key : No Sense [current] 
[ 1060.684813] sd 8:0:0:0: [sda] Add. Sense: No additional sense information
[ 1060.884422] kjournald starting.  Commit interval 5 seconds
[ 1060.897650] EXT3 FS on sda1, internal journal
[ 1060.897655] EXT3-fs: mounted filesystem with ordered data mode.

```

that was for the stuff related to the drive.

for *lsusb*:
```
Bus 002 Device 003: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c214 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
```
The Logitech one is my Logitech ATTACK 3 that i forgot to unplug :P

for *sudo fdisk -l*


```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000818cc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4866     1646662+   5  Extended
/dev/hda5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sda: 2199.0 GB, 2199023255040 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad54ad54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux

```

The strange part is, it works on the live CD, but not on the installation. Ill go back and check in the installed version while i wait for any more help, ill post if the problem somehow fixed itself.

[edit] strange, it works, however i did just do a update before I booted into the live CD. Regardless it works again so thank you so much. :)

---

