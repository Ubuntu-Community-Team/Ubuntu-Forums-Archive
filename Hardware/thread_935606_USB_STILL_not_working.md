---
title: "USB STILL not working"
date: 2008-10-01
forum: Hardware
---

### Post by Forbees on 2008-10-01
this is the old post . . . 3 pages long, but i'll summerize it
[http://ubuntuforums.org/showthread.php?t=930011&page=3](http://ubuntuforums.org/showthread.php?t=930011&page=3)

linux wont detect my flashdrive . . . . and apparently it thinks it is a floppy drive . . . i have no floppy drives on my computer

these are the codes was told to run

tell me what they mean >,<


```
forbees@forbees-desktop:~$ sudo fdisk -l
[sudo] password for forbees: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1188f42c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14611   117362826    7  HPFS/NTFS
/dev/sda3           14612       24321    77995575    f  W95 Ext'd (LBA)
/dev/sda5           14612       23990    75336786   83  Linux
/dev/sda6           23991       24321     2658726   82  Linux swap / Solaris 

```

```

forbees@forbees-desktop:~$ dmesg | tail
[ 6361.210361] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6361.210366] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6361.210369] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6361.210372] end_request: I/O error, dev sr0, sector 841024
[ 6361.210375] Buffer I/O error on device sr0, logical block 210256
[ 6372.197715] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6372.197720] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6372.197723] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6372.197726] end_request: I/O error, dev sr0, sector 841216
[ 6372.197729] Buffer I/O error on device sr0, logical block 210304
forbees@forbees-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c525 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=63d73897-55dd-498f-a9ff-30b296f3ee57 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=18239db6-75fc-49d0-a769-694d91d64f0f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```

forbees@forbees-desktop:~$ sudo mkfs.vfat -v /dev/fd0
[sudo] password for forbees: 
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0

```

---

### Post by knattlhuber on 2008-10-01
At the risk of suggesting what s/b else already did in the other thread:
With your memorystick plugged in, could you please run

```
lshw short -C disk
```

Is it only that one USB stick that's not working or any USB stick won't work?

---

### Post by Forbees on 2008-10-01
> **knattlhuber said:**
> 
Is it only that one USB stick that's not working or any USB stick won't work?

no usb file storage is detected my usb's light turns on for only a second, when it's supposed to stay on while it's plugged in

in ```
 dmesg | tail
lsusb
``` i posted (the second one) you can see that my USB mouse is detected and works fine

it also detects my lexmark x1270 scanner/printer (but can only scan cuz lexmark sucks like that)

```
forbees@forbees-desktop:~$ lshw short -C disk
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

```

i dont really see the point of that code :-/

---

### Post by knattlhuber on 2008-10-01
The point of that code is to tell you that I'm an idiot and dropped a hyphen from the syntax... :)

```
sudo lshw -short -C disk
```

---

### Post by Forbees on 2008-10-01
> **knattlhuber said:**
> The point of that code is to tell you that I'm an idiot and dropped a hyphen from the syntax... :)


seems you forgot the sudo too :-p

```
 forbees@forbees-desktop:~$ sudo lshw -short -C disk
[sudo] password for forbees: 
H/W path         Device      Class       Description
====================================================
/0/100/12/0      /dev/cdrom  disk        CDDVDW SH-S203N
/0/100/12/1      /dev/sda    disk        200GB ST3200826AS

```

seems to not detect my usb >,<

---

### Post by knattlhuber on 2008-10-01
Yah, forgot the sudo as well :)

I had thought that maybe the filesystem on that one USB is screwed up. But with the info you provided that is unlikely to be the case, especially since not even the kernel appears to see your drive. Sorry that I can't be of more help.

---

### Post by Forbees on 2008-10-04
so i tired intrepid beta hoping with the new driver supports and everything i might get some luck

but intrepid didn't detect them either >,<

---

