---
title: "USB Portable HD (Iomega): Can't mount."
date: 2008-12-12
forum: Hardware
---

### Post by steve_q on 2008-12-12
So I have an Iomega portable usb harddisk that I was using with WinXP, but now that I'm attempting to dual boot this system... I need access to this guy via Ibex, as well.  To add to the fun, it's formatted NTFS.

I've managed to get Ibex to see that something's there:
```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0582:0033 Roland Corp. EDIROL PCR
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 059b:0177 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```... and under Places>Computer, I see a USB drive present among my other internal storage devices.  However, when I attempt to mount it.. no dice.

Any ideas?

Thx in advance!  :)

---

### Post by tech9 on 2008-12-12
with your media disk plugged into your computer

try opening gnome-terminal

and type

 	Code:
 	sudo fdisk -l 
This should list all of your partitions / mounted devices.

Please post your output & we'll take it from there.

---

### Post by steve_q on 2008-12-12
> **tech9 said:**
> with your media disk plugged into your computer

try opening gnome-terminal

and type

     Code:
     sudo fdisk -l 
This should list all of your partitions / mounted devices.

Please post your output & we'll take it from there.
Thanks for the speedy reply!

Here's the output of fdisk -l```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b2e9896

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcae7cae7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6994    56179273+  83  Linux
/dev/sdb2            6995        7297     2433847+   5  Extended
/dev/sdb5            6995        7297     2433816   82  Linux swap / Solaris
```

---

### Post by The-Kernel on 2008-12-12
Try this at the command line:

sudo mount -a /dev/sda1 /media/sda1

if -a doesn't work, try -o

also, make sure /media/sda1 exist or at least the place that you're mounting it to does.

---

### Post by steve_q on 2008-12-12
> **The-Kernel said:**
> Try this at the command line:

sudo mount -a /dev/sda1 /media/sda1

if -a doesn't work, try -o

also, make sure /media/sda1 exist or at least the place that you're mounting it to does.
sda1 is an internal NTFS (WinXP)drive, already mounted.  Thanks.  :)

---

### Post by steve_q on 2008-12-12
Also, not sure if this helps nail it down for you guys:

When I leave the USB drive unconnected, Storage Device Manager (pysdm) will open
When I connect the usb cable to the drive and reboot 2 things happen:
1.  The loading bar pauses for an extended length of time at 15%..
2.  Storage Device Manager (pysdm) will not open.  (crashes)

Thanks again.

---

### Post by azzid on 2008-12-12
Google gave me [this]("http://www.linuxquestions.org/questions/mandriva-30/mount-an-external-ntfs-usb-hard-disk-201441/").

What you want from that is that you can use **dmesg** to figure out what device is your usb drive.

Plug the drive in and try:```
dmesg | grep SCSI
```

Also try giving mount the switch '-t ntfs', if that fails you might need to install some ntfs support.

---

### Post by tech9 on 2008-12-12
Try this at the command line:

```
sudo mount /dev/sdb1
```

---

### Post by steve_q on 2008-12-12
> **azzid said:**
> Google gave me [this]("http://www.linuxquestions.org/questions/mandriva-30/mount-an-external-ntfs-usb-hard-disk-201441/").

What you want from that is that you can use **dmesg** to figure out what device is your usb drive.

Plug the drive in and try:```
dmesg | grep SCSI
```Also try giving mount the switch '-t ntfs', if that fails you might need to install some ntfs support.
dmesg | grep SCSI
-- returns no results.

dmesg
-- returns so many results that I can't see the top of the list in terminal.
-- results look like this:
```
[ 3778.331304] sd 2:0:0:0: [sdc] Add. Sense: No additional sense information
[ 3778.334793] sd 2:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 3778.334802] sd 2:0:0:0: [sdc] Add. Sense: No additional sense information
[ 3778.338292] sd 2:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 3778.338302] sd 2:0:0:0: [sdc] Add. Sense: No additional sense information
[ 3778.341791] sd 2:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 3778.341800] sd 2:0:0:0: [sdc] Add. Sense: No additional sense information
[ 3778.345666] sd 2:0:0:0: [sdc] Sense Key : No Sense [current] 
[ 3778.345675] sd 2:0:0:0: [sdc] Add. Sense: No additional sense information
... continued for 100 more lines of identical Sense Key and Add. Sense info:  none

```

Any other ideas?

---

### Post by steve_q on 2008-12-12
> **tech9 said:**
> Try this at the command line:

```
sudo mount /dev/sdb1
```
sdb (and all of its partitions) are already mounted.
-- they're the physical (internal) drive that Ibex lives on.

---

### Post by azzid on 2008-12-12
The USB drive should pick the next available letter, if sda and sdb are taken it'll pick sdc. You know which is the next available letter?

---

### Post by azzid on 2008-12-12
The grep should return something like ```
SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)

``` but only if you just connected the drive as dmesg get "filled" quite fast.

Did you reconnect the drive before greping through dmesg?

---

### Post by tech9 on 2008-12-12
> **steve_q said:**
> sdb (and all of its partitions) are already mounted.
-- they're the physical (internal) drive that Ibex lives on.

I am sorry, I misread that... I meant 

```
sudo mount /dev/sda1
```

---

### Post by tech9 on 2008-12-12
> **azzid said:**
> The USB drive should pick the next available letter, if sda and sdb are taken it'll pick sdc. You know which is the next available letter?

this is a good point... it's worth a shot trying to mount it as sdc

---

### Post by steve_q on 2008-12-12
> **azzid said:**
> The USB drive should pick the next available letter, if sda and sdb are taken it'll pick sdc. You know which is the next available letter?
C would be the next available.  ;)

> **azzid said:**
> The grep should return something like ```
SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)

``` but only if you just connected the drive as dmesg get "filled" quite fast.

Did you reconnect the drive before greping through dmesg?
I disc'd/reconnected the cable prior to running dmesg, yes... tried it again, still returns no results.  :(

Not sure if it's an issue, but this is a USB, *IDE* drive, btw.
(also tried dmesg | grep IDE    =  No results.)

---

### Post by steve_q on 2008-12-12
> **tech9 said:**
> this is a good point... it's worth a shot trying to mount it as sdc
Tried that too.  No joy.

Perhaps I'm asking the wrong questions, or not providing the proper introductory info?

---

### Post by steve_q on 2008-12-12
bump

---

### Post by azzid on 2008-12-13
There should be something in the dmesg, this is my output from just trying it myself:
```
**root@virtuous:~# dmesg | grep "SCSI device"**
[   13.194528] SCSI device sda: 41943040 512-byte hdwr sectors (21475 MB)
[   13.195052] SCSI device sda: 41943040 512-byte hdwr sectors (21475 MB)
[  202.969403] SCSI device sdb: 1953525168 512-byte hdwr sectors (1000205 MB)
[  203.026922] SCSI device sdb: 1953525168 512-byte hdwr sectors (1000205 MB)

```

I get both sda and sdb in the output due to that disk being a little bit special, with a normal drive you would only get one drive-id, like sdb, and should then be able to mount sdb1.

---

### Post by azzid on 2008-12-13
Now I tried to plug my usb-stick in instead of the harddrive:
```
root@virtuous:~# dmesg | grep "SCSI device"
[  907.584340] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[  907.681835] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)

```

The same command works like a charm, so it seems all the usb storage devices are treated in the same way.

---

### Post by steve_q on 2008-12-13
Honestly.. I don't get ANY results from dmesg | grep "SCSI device".  I just goes back to prompt.
```
root@steven-desktop:/home/steven# dmesg | grep "SCSI device"
root@steven-desktop:/home/steven#
```

Is there another type of device I might be needing to grep?

:(

---

### Post by steve_q on 2008-12-17
bump again (last one, sorry.)

---

