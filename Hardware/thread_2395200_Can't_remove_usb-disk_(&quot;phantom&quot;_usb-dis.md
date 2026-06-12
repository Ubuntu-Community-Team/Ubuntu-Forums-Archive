---
title: "Can't remove usb-disk (&quot;phantom&quot; usb-disk)"
date: 2018-06-28
forum: Hardware
---

### Post by aaltom on 2018-06-28
Hi all,
just testing out ubu18 and came over this problem:
I use a sd-card with an usb-sd converter, to be able to write etc. to sd-card.
Now in the new release (18 server), if I insert the usb-disk and dmesg i get a usual:

[91496.081949] sd 8:0:0:0: Attached scsi generic sg1 type 0
[91496.188057] sd 8:0:0:0: [sdb] 30572544 512-byte logical blocks: (15.7 GB/14.6 GiB)
[91496.190024] sd 8:0:0:0: [sdb] Write Protect is off
[91496.190027] sd 8:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[91496.192056] sd 8:0:0:0: [sdb] No Caching mode page found
[91496.193999] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[91496.202996]  sdb: sdb1 sdb2
[91496.208060] sd 8:0:0:0: [sdb] Attached SCSI removable disk

And when I remove it, I get as usual:
[91573.261732] usb 2-2: USB disconnect, device number 11

The drive itself is not working, because there is in some way locked in the system a "phantom" usb-disk ?
Because when I physically remove the disk and do fdisk I get:
*****************
fdisk /dev/sdb

Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sdb: 1.4 GiB, 1542815744 bytes, 3013312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8d5e5979

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1        8192 6143999 6135808  2.9G 83 Linux
*****************

There is NO sdb1 physically in the pc !
I can even write a new p-table to the "phantom" usb-disk... but how do I get rid of it !?
What the heck is happening ? Some kind of cache somewhere ? If so who forgot to flush it or whatever ?
BTW. I can't reboot this machine, IT'S A SERVER.


br. Mike

---

### Post by ajgreeny on 2018-06-28
Did you remove it properly by first unmounting the device's partition(s) or did you just pull it out?

---

### Post by aaltom on 2018-06-28
I never mounted anything from it, I just inserted it physically.
I only it for dd:ing images to it etc., never mounts.
And also just removed it physically. 

I have done this many 1000-times in many different distros,
but never faced this before...

---

### Post by aaltom on 2018-08-07
Hi,
after a LOOOONG time, nothing ?
So this UBU 18-thingy is HIGHLY BETA-BETA-BETA-BETA !!!! Don't wanna touch this even with a long stick !

My own solution:
Will degrade asap.... to 16...
Just forget this.... and a big waste of effort.



br. Mike

---

