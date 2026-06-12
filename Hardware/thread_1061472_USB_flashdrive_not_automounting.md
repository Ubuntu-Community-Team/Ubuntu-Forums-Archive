---
title: "USB flashdrive not automounting"
date: 2009-02-05
forum: Hardware
---

### Post by DarkReverend on 2009-02-05
I have Kubuntu 7.10 upgraded to 8.04 (apparently.  don't know why it doesn't go up to 8.10) as shown by /etc/issue:

```
$ cat /etc/issue
Ubuntu 8.04.2 \n \l

```

my usb flashdrives mounted fine after a safe upgrade, but then I finally preformed the full upgrade and they are no longer automounting.

the device appears in /dev, I got sudo blkid and sudo fdisk -l from another thread, and they look fine to me (/dev/sdc1  is the flashdrive)
```
$ sudo blkid
/dev/sda1: UUID="36d6b9e2-4892-4e06-b6ac-265eade82f97" SEC_TYPE="ext2" TYPE="ext
3"
/dev/sda2: UUID="6afa3cd6-603c-421c-8824-e1d776be1f3f" SEC_TYPE="ext2" TYPE="ext
3"
/dev/sda3: TYPE="swap" UUID="06c299f4-afe6-4881-9e53-0bf7b4be0e30"
/dev/sdb2: UUID="a314fda2-7446-4925-a38d-83ecb744356a" SEC_TYPE="ext2" TYPE="ext
3"
/dev/sdc1: SEC_TYPE="msdos" UUID="C2F8-E4F2" TYPE="vfat"

``````
$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1457

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9118    73240303+  83  Linux
/dev/sda2            9119       30276   169951635   83  Linux
/dev/sda3           30277       30401     1004062+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac16c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1       30276   243191938+  83  Linux

Disk /dev/sdc: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         946      983024    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(960, 64, 32) logical=(945, 14, 32)

```

I think the problem is something wrong with hal, but it could be where the issue is just presenting itself.  the hal service claims not to be running in system settings -> services, but if I try to start it, it gives the error it's already running.  My media shows devices it should not be, and if I click on the CD, for example, it says that I need to have HAL running to use the feature.

```
$ ps -ef | grep hal
107       8379     1  0 01:30 ?        00:00:00 /usr/sbin/hald
root      8380  8379  0 01:30 ?        00:00:00 hald-runner
107       8406  8380  0 01:30 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      8426  8380  0 01:30 ?        00:00:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event2 /dev/input/event1
root      8451  8380  0 01:30 ?        00:00:00 hald-addon-storage: polling /dev/hda (every 2 sec)
root     10523  8380  0 01:50 ?        00:00:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
robert   11143 10920  0 02:07 pts/3    00:00:00 grep hal

```

I'm at my limit - I need help.

---

### Post by DarkReverend on 2009-02-10
It's been 4 days and this has fallen past page 20.  I really do need a hand here.  at the very least, if there's a better place to put this topic, let me know so I can ask in a better place.

---

### Post by Sk8man on 2009-02-10
can u mount it manually?

---

### Post by DarkReverend on 2009-02-10
No, it doesn't look like it.  I tried using the following command 
(directory created):  ```
sudo mount -t vfat /dev/sdc /home/robert/usbtemp
``` 


and got the following results (dmesg)
```
[433509.676251] usb 6-6: reset high speed USB device using ehci_hcd and address 8
[433710.982584] FAT: invalid media value (0xb9)
[433710.982589] VFS: Can't find a valid FAT filesystem on dev sdc.
[433772.995066] usb 6-7: USB disconnect, address 9
[434066.197864] usb 6-7: new high speed USB device using ehci_hcd and address 10
[434066.370878] usb 6-7: configuration #1 chosen from 1 choice
[434066.400231] scsi9 : SCSI emulation for USB Mass Storage devices
[434066.402632] usb-storage: device found at 10
[434066.402636] usb-storage: waiting for device to settle before scanning
[434071.398351] usb-storage: device scan complete
[434071.399441] scsi 9:0:0:0: Direct-Access     Sony     Storage Media    0100 PQ: 0 ANSI: 0 CCS
[434071.401802] sd 9:0:0:0: [sdc] 1966080 512-byte hardware sectors (1007 MB)
[434071.402544] sd 9:0:0:0: [sdc] Write Protect is off
[434071.402548] sd 9:0:0:0: [sdc] Mode Sense: 43 00 00 00
[434071.402550] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[434071.413169] sd 9:0:0:0: [sdc] 1966080 512-byte hardware sectors (1007 MB)
[434071.413914] sd 9:0:0:0: [sdc] Write Protect is off
[434071.413919] sd 9:0:0:0: [sdc] Mode Sense: 43 00 00 00
[434071.413921] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[434071.413930]  sdc: sdc1
[434071.414770] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[434071.414820] sd 9:0:0:0: Attached scsi generic sg2 type 0
[434091.194087] FAT: invalid media value (0xb9)
[434091.194094] VFS: Can't find a valid FAT filesystem on dev sdc.
[434117.962023] usb 6-7: USB disconnect, address 10
[434124.513161] usb 6-7: new high speed USB device using ehci_hcd and address 11
[434124.648405] usb 6-7: configuration #1 chosen from 1 choice
[434124.667546] scsi10 : SCSI emulation for USB Mass Storage devices
[434124.667830] usb-storage: device found at 11
[434124.667835] usb-storage: waiting for device to settle before scanning
[434129.679474] usb-storage: device scan complete
[434129.680440] scsi 10:0:0:0: Direct-Access     I0MEGA   UMni64MB*IOM2C4       PQ: 0 ANSI: 2
[434129.681802] sd 10:0:0:0: [sdc] 126976 512-byte hardware sectors (65 MB)
[434129.682424] sd 10:0:0:0: [sdc] Write Protect is off
[434129.682431] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[434129.682433] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[434129.692543] sd 10:0:0:0: [sdc] 126976 512-byte hardware sectors (65 MB)
[434129.693167] sd 10:0:0:0: [sdc] Write Protect is off
[434129.693174] sd 10:0:0:0: [sdc] Mode Sense: 03 00 00 00
[434129.693176] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[434129.693185]  sdc: sdc1
[434129.695123] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[434129.695170] sd 10:0:0:0: Attached scsi generic sg2 type 0
[434136.281363] FAT: invalid media value (0x01)
[434136.281370] VFS: Can't find a valid FAT filesystem on dev sdc.

```

The flash drive is FAT - tested on a windows computer.  Also, i tried two separate flashdrives, no go.

fdisk -l output:
```
Disk /dev/sdc: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         946      983024    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(960, 64, 32) logical=(945, 14, 32)

```

---

### Post by DarkReverend on 2009-02-13
update: 

if I browse to system:/media/, and try to get into anything, even my hard drives, I get "this feature only available with Hal"

---

### Post by DarkReverend on 2009-02-15
I'm still looking for help on this issue.

---

### Post by ben44b on 2009-02-17
Do you have usbmount installed?

Just a stab in the dark...

---

### Post by DarkReverend on 2009-02-21
I do not, however, this functionality was working previously, I can manually mount the device, and the package description for usbmount states that it is a lightweight framework and recommends hal for automounting.

appreciate the idea though.

---

### Post by drinkpepsi on 2009-02-21
Maybe this will work? Post #6
[http://ubuntuforums.org/showthread.php?t=151945](http://ubuntuforums.org/showthread.php?t=151945)

---

### Post by dvlong on 2009-02-26
The problem you describe is nearly exactly like the problem I'm having. Any usb drive (portable hard drive, mp3, flash, etc) would not mount, automatically or manually.  The forums I've been looking in have a scattering of information that seems to touch on this but nothing I've found that works. 

I agree that the problem seems related to hal - so I wonder what happens if you try to find a different version of hal and use that?

---

### Post by freund on 2009-02-27
I have the same issue with a usb harddrive. log files look the same. It mounts OK 8.04 but not in 8.10. I have other USB harddrives that mount fine in 8.10. 8.04 and 8.10 are on the same computer HD but separate partions, so it can't be the hardware. I also suspect HAL and am looking for a solution also. I will let you know if I find one.:confused:

---

### Post by ponyexpress on 2009-03-06
I had the same problem.
Delete the /etc/fstab entry for your flash drive

[COLOR="Blue"]/dev/sdc1: SEC_TYPE="msdos" UUID="C2F8-E4F2" TYPE="vfat"[/COLOR]

and it should automount again and show up in your /media folder.

---

### Post by DarkReverend on 2009-03-07
I'm having the same problem with my CDRom.  its in fstab but won't automount.  MyUSB is not in fstab, and also refuses to automount.

---

### Post by ymo on 2009-03-07
> **DarkReverend said:**
> I have Kubuntu 7.10 upgraded to 8.04 (apparently.  don't know why it doesn't go up to 8.10) as shown by /etc/issue:

```
$ cat /etc/issue
Ubuntu 8.04.2 \n \l

```


8.04 is LTS (long term support) while 8.10 is not. Because of this, 8.10 will not be automatically offered as an upgrade to 8.04.

See [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) for info on how to upgrade 8.04 -> 8.10.

---

### Post by DarkReverend on 2009-03-08
> **ymo said:**
> 8.04 is LTS (long term support) while 8.10 is not. Because of this, 8.10 will not be automatically offered as an upgrade to 8.04.

See [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) for info on how to upgrade 8.04 -> 8.10.

Thanks for this info, however, this doesn't solve my root problem.

---

### Post by DarkReverend on 2009-04-25
I have finally found out what my issue was

[http://ubuntuforums.org/showpost.php?p=5675742&postcount=11](http://ubuntuforums.org/showpost.php?p=5675742&postcount=11)

polkit-auth --user user --grant org.freedesktop.hal.storage.mount-removable wasn't the problem, though, it was org.freedesktop.hal.storage.mount-fixed that needed to be added.  i have no idea how this got changes, or what USB flashdrives are fixed, but adding this permission solved my problem.

---

