---
title: "Unable to detect/mount Samsung 640Gb USB harddrive"
date: 2016-02-17
forum: Hardware
---

### Post by klark2 on 2016-02-17
I have read several threads regarding detecting / mounting, to no avail. I'm hoping you awesome people can help me...

I am running Ubuntu 14.04 on a HP Notebook. Attempting to use my Samsung 640Gb USB harddrive. When plugged in, it is not recognized or mounted. Here is the information I was able to gather.

fdisk -l[COLOR=#ff0000]*** <<< THE ONLY DEVICE THAT SHOWS UP IS MY INTERNAL HARD DRIVE***[/COLOR]
klark@klark-HP-Notebook:~$ sudo fdisk -l
[sudo] password for klark: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x8ad5e980

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

****************************************
lsusb
klark@klark-HP-Notebook:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b52d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0a5c:216d Broadcom Corp. 
Bus 001 Device 004: ID 04e8:60b4 Samsung Electronics Co., Ltd [COLOR=#ff0000]*** <<< THIS IS THE DEVICE IN QUESTION***[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

*******************************************
dmesg | tail -n 20[COLOR=#ff0000]***   <<< THIS COMMAND WAS USED WHEN DEVICE WAS PLUGGED IN FOR ALMOST AN HOUR***[/COLOR]
klark@klark-HP-Notebook:~$ dmesg | tail -n 20
[  691.356642] sd 2:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  691.356655] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current]
[  691.356661] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  691.356665] sd 2:0:0:0: [sdb] CDB: 
[  691.356668] Read(10): 28 00 00 00 00 00 00 00 08 00
[  691.356686] blk_update_request: critical medium error, dev sdb, sector 0
[  691.356694] Buffer I/O error on dev sdb, logical block 0, async page read
[  693.265724] sd 2:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  693.265736] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current]
[  693.265741] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  693.265745] sd 2:0:0:0: [sdb] CDB: 
[  693.265748] Read(10): 28 00 00 00 00 00 00 00 20 00
[  693.265765] blk_update_request: critical medium error, dev sdb, sector 0
[  694.941187] sd 2:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  694.941198] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current]
[  694.941203] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  694.941206] sd 2:0:0:0: [sdb] CDB: 
[  694.941209] Read(10): 28 00 00 00 00 00 00 00 08 00
[  694.941224] blk_update_request: critical medium error, dev sdb, sector 0
[  694.941231] Buffer I/O error on dev sdb, logical block 0, async page read

***********************************************
[COLOR=#ff0000]***I USED THE SAME COMMAND BUT JUST AFTER UNPLUGGING AND REPLUGGING THE HARD DRIVE***[/COLOR].
klark@klark-HP-Notebook:~$ dmesg | tail -n 20
[  691.356655] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current]
[  691.356661] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  691.356665] sd 2:0:0:0: [sdb] CDB: 
[  691.356668] Read(10): 28 00 00 00 00 00 00 00 08 00
[  691.356686] blk_update_request: critical medium error, dev sdb, sector 0
[  691.356694] Buffer I/O error on dev sdb, logical block 0, async page read
[  693.265724] sd 2:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  693.265736] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current]
[  693.265741] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  693.265745] sd 2:0:0:0: [sdb] CDB: 
[  693.265748] Read(10): 28 00 00 00 00 00 00 00 20 00
[  693.265765] blk_update_request: critical medium error, dev sdb, sector 0
[  694.941187] sd 2:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  694.941198] sd 2:0:0:0: [sdb] Sense Key : Medium Error [current]
[  694.941203] sd 2:0:0:0: [sdb] Add. Sense: Unrecovered read error
[  694.941206] sd 2:0:0:0: [sdb] CDB: 
[  694.941209] Read(10): 28 00 00 00 00 00 00 00 08 00
[  694.941224] blk_update_request: critical medium error, dev sdb, sector 0
[  694.941231] Buffer I/O error on dev sdb, logical block 0, async page read
[  965.476857] usb 1-3: USB disconnect, device number 4   [COLOR=#ff0000]***<<<  DOES THIS LINE HELP? ***[/COLOR]

---

### Post by weatherman2 on 2016-02-17
Are you plugging it into a USB 2 or USB 3 port?  Do other devices work when plugged into that USB port?

Are you sure the drive itself is good?  Does it work on other computers or in Windows?  If you don't know if the drive is good, you might check it's S.M.A.R.T. status with GSmartControl, to see if it is detected at all.

Is this a portable drive (no power cord - self-powered by the USB cable only) or does it have its own power supply?  If powered only by USB, sometimes one USB port on a laptop doesn't provide enough power to power a hard drive.  Some of these drives have "Y" connectors so you can plug into two USB ports to get 2X the power.  Newer laptops tend to have enough power on one USB port, but if the laptop is 5-6 years old, maybe not.

---

### Post by klark2 on 2016-02-17
I have tried all three USB2 ports on the laptop, with no results. Other devices work well when plugged into the ports.
The drive works on Windows. ( I use it for storage ). 
Yes, it is a portable drive with no power cord.

When I had Windows installed on THIS laptop, the HD worked fine. Also, the command lsusb showed the HD in question. Can I use that information in any way to mount it?

Thank you for your assistance.

---

### Post by weatherman2 on 2016-02-17
If the drive is indeed good now and it worked before on this same laptop with Windows, then there is something busted and you probably won't be able to just mount it.

I hear about these incompatibility problems sometimes with external drives in Ubuntu, but I guess I've been lucky - I have plugged in lots of different USB drives and enclosures and either they mount automatically or I can find them in a Nautilus window and click the name of the drive to mount.  No magic necessary.

So I assume there is some incompatibility with this particular drive.  You might boot a newer version of Ubuntu and see how it works with that.

The drive isn't encrypted, is it?  If so, that would explain your problem.

---

