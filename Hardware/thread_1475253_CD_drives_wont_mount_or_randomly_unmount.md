---
title: "CD drives wont mount or randomly unmount"
date: 2010-05-06
forum: Hardware
---

### Post by anivegmin on 2010-05-06
When I start my Ubuntu Lucid system both cd rom drives work fine; then after what seems like a random length of time - anything from minutes to hours - they will both become inaccesible. They will either unmount cd's already in the drawers or refuse to mount newly inserted discs

$ sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=16931e94-ed47-474e-812a-62539e100e29 / ext4 defaults 0 1
# swap was on /dev/sda5 during installation
UUID=4dfcdf04-940a-4215-8309-83bed499f55c swap swap sw 0 0
/dev/fd0 /media/floppy0 vfat noauto 0 0

$ ls -l /dev/{cd,dvd}*

lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrom -> sr1
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrom1 -> sr0
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrw -> sr1
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/cdrw1 -> sr0
lrwxrwxrwx 1 root root 3 2010-05-06 13:34 /dev/dvd1 -> sr0

sudo hdparm -I /dev/{sr0,sr1}

/dev/sr0:

ATAPI CD-ROM, with removable media
	Model Number:       TSST CD-RW/DVD-ROM TSH492B              
	Serial Number:      
	Firmware Revision:  TB04    
Standards:
	Supported: CD-ROM ATAPI-1 -2 -3 
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	    	PACKET command feature set
	    	DEVICE_RESET command
	   *	DOWNLOAD_MICROCODE
	    	Removable Media Status Notification feature set
HW reset results:
	CBLID- above Vih
	Device num = 0

/dev/sr1:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-ST GCE-8320B                      
	Serial Number:      
	Firmware Revision:  1.01    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 *mdma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=227ns  IORDY flow control=120ns

After the drives have unmounted or fail to mount -

$ sudo hdparm -I /dev/{sr0,sr1}

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange

/dev/sr1:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange

Help please.

---

### Post by anivegmin on 2010-05-08
OK after much fiddling and headbanging -

Swapping cables, cleaning lens's etc.

Searching endlessly on forums, editing fstab, installing mount manager; all to no avail.

Tried disconnecting second cd drive (which i don't really need anyway) and now everything works perfectly.

For some reason Ubuntu couldn't cope with having 2 cd/dvd drives connected at the same time, obviously causing some sort of software conflict resulting in random unmounting or just not mounting discs at all. Also caused occasional crash of Docky when ejecting a disc.

Anyway now all is fine !

---

### Post by anivegmin on 2010-05-11
Spoke too soon !

Same problem.

Opened up the computer and checked all IDE connections and device jumper settings.

Both drives show up in BIOS.

Both drives work fine in Windows (which I want to get rid of)

Both drives show up in Disk Utility.

They always work immediately after starting computer - just randomly become inaccessible or wont mount while still showing up as drives in Disk Utility, but with "no medium detected"

Somebody please help me.

---

### Post by dr4c4n on 2010-05-31
I'm having exact same problem. Somewhere on another forum, it said also to remove all floppy entries from the bios, I have tried all of the software fixes, the /etc/fstab entries, as well as changing the bios, all to no avail. This is a serious problem and I hope it's resolved quickly so i do not have to downgrade back to 9.10. This is a very basic requirement for an operating system. I do not understand why it unmounts at random intervals?? what could be causing this?

---

### Post by anivegmin on 2010-06-13
This is it - problem solved at last !

This thread - [http://http//ubuntuforums.org/showthread.php?t=1502874](http://http//ubuntuforums.org/showthread.php?t=1502874)

Follow these instructions - [https://wiki.ubuntu.com/KernelTeam/M...MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/M...MainlineBuilds) for installing the 2.6.34 kernel.

Updating the kernel has fixed the problem for me.
Hurray !

---

### Post by anivegmin on 2010-06-15
Again I got carried away !!!!

Kernel upgrade did not work !!!!!

Problem is worse than ever now !!!!!!!!

I am getting seriously pissed off now !!!!!!!!!!!

This is a major show stopping problem that a lot of other users seem to be experiencing. See various other threads and bug reports.

Why isn't it being fixed ?

---

### Post by anivegmin on 2010-08-05
Well the latest kernel (2.6.35) was released for Ubuntu a couple of days back. After a couple of days testing this has DEFINITELY solved my CD/DVD mounting problems.

Add ppa:kernel-ppa/ppa to your software source list

Reload - then search for "2.6.35" in Synaptic.

Install the following 3 packages (make sure you choose the correct 3 for either 32 or 64 bit. 14 is the latest in the repository so this may change)

linux-headers-2.6.35-14
linux-headers-2.6.35-14-generic
linux-image-2.6.35-14-generic

This kernel will now be the default. Everything now works for me and I have had no problems with it.

---

