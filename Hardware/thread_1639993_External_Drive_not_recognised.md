---
title: "External Drive not recognised"
date: 2010-12-07
forum: Hardware
---

### Post by dhkillian on 2010-12-07
Greetings
I have just reinstalled my desktop with Ubuntu 10.10 - the Maverick Meerkat, dual booting with XP. I have had Ubuntu installed for a year, but wanted to be able to dual boot. During that time I was using a Fujitsu Siemans Storagebird external drive for back up without any problem. Before I reinstalled I backed up everything to this external drive. 
The problem I have now is that I cannot get either OS to see the external drive.I have pasted the results from FDISK -L and LSUSB below. Has anyone any ideas? I badly need this backed up data for work. Very grateful for any help.
Regards
DHK

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000f13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14551   116878188    7  HPFS/NTFS
/dev/sda2           14551       38914   195692545    5  Extended
/dev/sda5           14551       38149   189548544   83  Linux
/dev/sda6           38149       38914     6142976   82  Linux swap / Solaris

Disk /dev/sdg: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x688e77f4

   Device Boot      Start         End      Blocks   Id  System


Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 002 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 002: ID 050d:615a Belkin Components 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04b8:0813 Seiko Epson Corp. Stylus CX6500/6600
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Hippytaff on 2010-12-07
Hi, welcome to the forums
> 
Bus 002 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P

Is this a different device?
 
Have you tried manually mounting the usb storage device? does it appear when you type
```

mount

```

---

### Post by dhkillian on 2010-12-07
Hi Happy Taff
When I unplug the StorageBird, this line does not appear, so I guess it refers to the external drive. Not sure I understand how to "Mount"
Many thanks
Derek

---

### Post by dhkillian on 2010-12-07
Hi Happy Taff
This is what I get when I type Mount, and the JMicron device name. Is this right?

derek@derek-Vostro-200:~$ mount Bus 002 Device 010: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
mount: only root can do that

Regards
DHK

---

### Post by Hippytaff on 2010-12-07
Looks like it is mounted...can you acces it via the terminal?
```

cd /media

```
```

ls -a

```
does it appear after you do ls -a?
 
When you go to system -> administration -> additional drivers
 
does it offer any drivers for the device?

---

### Post by dhkillian on 2010-12-07
Hi
The only media listed is the cd rom. When I us the "l" command it shops what is in the CD ROM.
THe only additional drivers available from the list are for the NVIDIA graphics cared which I have loaded.

I really can't understand why it is not being seen. Prior to my reinstalling, it worked perfectly!

Kind regards
Derek

---

### Post by Hippytaff on 2010-12-07
How frustrating!
with it plugged in try
```

sudo apt-get update && sudo apt-get upgrade

```
 
Does it work in *gulp* windows?

---

### Post by coffeecat on 2010-12-07
@dhkillian, it seems as though you haven't posted the whole output of 'sudo fdisk 'l'. There are no partitions listed for sdg, just a column header. Please confirm whether or not there was anything else - it is impossible to advise you properly without knowing what is on sdg, if that is indeed the Fujitsu drive. 400GB? Is that right? Also, I wonder why there is no sdb, sdc, sde, and sdf. I presume they might be the TEAC multi-card reader. Does it have 4 slots?

Also - please enclose terminal output within [noparse]```

```[/noparse] tags. There is useful formatting in the output of fdisk which is lost when you don't. You can either type [noparse]```

```[/noparse] by hand and paste the output between them, or use the # button in the message toolbar.

---

### Post by dhkillian on 2010-12-08
Hi Coffeecat.
Thanks for the reply. Not sure what "sdg" is. External drive is a Fujitsu Siemens StorageBird 400GB. (actual drive in the casing is Magnetic Data Technologies) Do not know what "sdb, sdc, sde, and sdf" refer to. TEAC card reader has four slots.

Do not understand your final re [code]/[code] tags. I have pasted results from "sudo fdisk -l" below as they appear on my terminal screen.
Many thanks for your help.
DHK

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000f13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14551   116878188    7  HPFS/NTFS
/dev/sda2           14551       38914   195692545    5  Extended
/dev/sda5           14551       38149   189548544   83  Linux
/dev/sda6           38149       38914     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x688e77f4

   Device Boot      Start         End      Blocks   Id  System

---

### Post by coffeecat on 2010-12-08
> **dhkillian said:**
> Do not understand your final re [code]/[code] tags.

[See here](http://ubuntuforums.org/misc.php?do=bbcode#code)

Or the use of the # button makes it very simple.

---

### Post by dhkillian on 2010-12-08
........coffeecat
What do you want me to type on the terminal command line?
Regards
DHK

---

### Post by coffeecat on 2010-12-08
Sorry, posted the above accidentally before going on to your problem.

> **dhkillian said:**
> Not sure what "sdg" is.

....

Do not know what "sdb, sdc, sde, and sdf" refer to. TEAC card reader has four slots.

sda, sdb, etc refer to physical drives, whether they be internal hard drive, external hard drives, flash drives, or the physical devices in a card reader, which is why I asked you how many slots were in the TEAC. They appear in the order in which they are detected by the system. I was wanting to identify your problem USB drive in the fdisk output. The fact that the TEAC has four slots explains the missing sdb, c, d and e, but not the missing sdf, because your Fujitsu appeared as sdg.

Anyway, your output this time shows the Fujitsu as sdb so you must have removed the card reader and whatever was sdf last time. The bad news is that the partition that was on your external drive is not showing. You have a valid partition table - if you didn't you would get a 'no valid partition table' message - but no detectable partition. **That is, if you are sure you have posted the complete output.**

This is serious but not irrecoverable. Have a look here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can install testdisk from Ubuntu Software Centre to your Ubuntu and run it from the terminal. It should be able to find the missing partition and recreate the partition table entry so that you can recover the data. Also included in testdisk is the utility photorec. This is used for recovering files when a partition cannot be recovered. **Do not use this yet**. Try testdisk first.

---

### Post by dhkillian on 2010-12-08
Coffecat
Followed your instructions and,............YIPEE!! It works! Many, many thanks.
This is what I find so great about the Linux community. People work together to fix problems, those with the knowledge help those who need it. Society at large would benefit from this ethos.
Again, many thanks
God bless
DHK

---

### Post by coffeecat on 2010-12-08
Glad it's sorted. Enjoy Ubuntu.

---

