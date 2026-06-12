---
title: "external hard drive (Lacie) not being detected"
date: 2015-07-01
forum: Hardware
---

### Post by bowie101 on 2015-07-01
Hi all. This used to work, now it does not. Lacie external hard drive is not being detected. Lubuntu 12.10 (I think. whatever the LTS version is) 

The hard drive works with my windows machine still. The other things that I plug into this Lubuntu machine are detected. This machine is a toshiba netbook (nb205). 
-----------------------------
 ```


sudo fdisk -l  

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   113055743    56526848   83  Linux
/dev/sda2       113057790   117229567     2085889    5  Extended
/dev/sda5       113057792   117229567     2085888   82  Linux swap / Solaris



xian-NB205:~$ dmesg | tail


[21433.396099] usb 5-2: device descriptor read/64, error -71
[21433.612155] usb 5-2: new full-speed USB device number 3 using uhci_hcd
[21433.736088] usb 5-2: device descriptor read/64, error -71
[21433.964097] usb 5-2: device descriptor read/64, error -71
[21434.180137] usb 5-2: new full-speed USB device number 4 using uhci_hcd
[21434.596064] usb 5-2: device not accepting address 4, error -71
[21434.708103] usb 5-2: new full-speed USB device number 5 using uhci_hcd
[21435.124069] usb 5-2: device not accepting address 5, error -71
[21435.124113] hub 5-0:1.0: unable to enumerate USB device on port 2
[21437.229571] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:bc:c8:10:06:ae:8e:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 

```

I even think that I caught it working for a second before i messed it up. After 5 min of the hard drive being plugged in did I get a message. But I cant swear to it, b/c I moved my hands too fast in changing it up. 


help?

---

### Post by dino99 on 2015-07-02
as the dmesg suggests, pay attention to the usb bios/uefi settings. Should be good to know which kind of usb it is (1 or 2 or 3) both on hdd and mobo
is that happening with an already hdd plugged before booting, or plugged after boot ?

---

### Post by bowie101 on 2015-07-07
it looks just like this [http://www.filmtools.com/lacie-rugged-hard-disk-triple-usb-3-1tb.html](http://www.filmtools.com/lacie-rugged-hard-disk-triple-usb-3-1tb.html) but i got it from someone else back in 2011 so it is either usb2 or 3. how can i tell? i would boot first and then plug in.  bios for usb? as in the order for looking at where to boot from? that will be new territory for me with this machine. I can look at it, for sure. What is suggested next step?

---

### Post by CharlesA on 2015-07-07
If it is from 2011, it is likely USB2. USB3 hard drives use a different type of cable and the connectors are usually blue.

---

### Post by bowie101 on 2015-07-07
about a year ago, I called up the lacie people, to send me a rep

ement cord. After taking all my info, serial number, etc. they send me a cord, on which it says usb 3. But maybe they are sending me just the latest of what they have in stock, knowing it will be backwards compatible. But what determines the standard being used, the cord, or the external hard drive, itself? 
 
At any rate, I just plugged in the hard drive as I booted and it made intermittent chirping noises as this computer started up and then got through it's boot up cycle. Once in its normal on state, after a few minutes, the intermittant chirping stopped. the drive is still not recognized, and yet, I feel the current running through it, and hear the hard drive's little clicking that a hard drive does. Again, it used to work here, and it works on my windows machines. 


...wait, so then I get this .. 

```


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6814b6c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488386646   244193292   af  HFS / HFS+
/dev/sdb2       488386710   976773167   244193229    b  W95 FAT32
xian-NB205:~$ 


```

and then when i try to mount it, it said it doesn't exist. So then i repeat the above code, and indeed, the hard drive is back to not being detected. Then, about 10 minutes or more into the computer being on and the hard drive plugged in, after all these commands, and 1 or 2 failed mounting commands, on it's own, it mounts and is viewable in the file manager.....and as I type, minutes go by, and once again, the fdisk command indicates no detection. 

```
   




Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   113055743    56526848   83  Linux
/dev/sda2       113057790   117229567     2085889    5  Extended
/dev/sda5       113057792   117229567     2085888   82  Linux swap / Solaris



xian-NB205:~$ dmesg | tail
[ 1131.080389] usb 1-8: USB disconnect, device number 30
[ 1131.120363] sd 28:0:0:0: [sdb] Synchronizing SCSI cache
[ 1131.120512] sd 28:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1137.963016] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c4:01:7c:0d:62:00:08:00 SRC=10.0.0.67 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xA0 TTL=1 ID=23638 PROTO=2 
[ 1201.732152] usb 1-8: new high-speed USB device number 31 using ehci_hcd
[ 1201.899823] scsi29 : usb-storage 1-8:1.0
[ 1202.100009] usb 1-8: USB disconnect, device number 31
[ 1263.506274] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c4:01:7c:0d:62:00:08:00 SRC=10.0.0.67 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xA0 TTL=1 ID=65328 PROTO=2 
[ 1394.608159] usb 1-8: new high-speed USB device number 32 using ehci_hcd
[ 1394.676354] hub 1-0:1.0: unable to enumerate USB device on port 8
xian-NB205:~$ 



    
``` 


and then it came back in file manager, and then i typed fdisk again 

and it says

```


 xian-NB205:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   113055743    56526848   83  Linux
/dev/sda2       113057790   117229567     2085889    5  Extended
/dev/sda5       113057792   117229567     2085888   82  Linux swap / Solaris
fdisk: unable to read /dev/sdb: Invalid argument
 
``` 

...because it is no longer detected. So the whole thing is very intermittent, and it seems like it spend more time not being detected then being detected and mounted. 

what to do?

---

### Post by bowie101 on 2015-07-07
I might note that while the hard drive is sitting still on a table, the laptop/netbook is, of course, on my lap. So the laptop isn't perfectly still, but while I suspect the cord is the problem, I also don't think it's the problem. I can still feel the current running into it, all througout this.  Buuuutt, I am now swapping out the cord and the hard drive with my other, and then just bringing back the hard drive with a swapped out cord....detected rather immediately. So, maybe it is the cord after all..


```



xian-NB205:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00064e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   113055743    56526848   83  Linux
/dev/sda2       113057790   117229567     2085889    5  Extended
/dev/sda5       113057792   117229567     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6814b6c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488386646   244193292   af  HFS / HFS+
/dev/sdb2       488386710   976773167   244193229    b  W95 FAT32

....

xian-NB205:~$ dmesg | tail
[ 2625.100508] sd 33:0:0:0: Attached scsi generic sg1 type 0
[ 2625.109225] sd 33:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 2625.110096] sd 33:0:0:0: [sdb] Write Protect is off
[ 2625.110106] sd 33:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 2625.112750] sd 33:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2625.145416]  sdb: sdb1 sdb2
[ 2625.149139] sd 33:0:0:0: [sdb] Attached SCSI disk
[ 2625.867249] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[ 2640.385561] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c4:01:7c:0d:62:00:08:00 SRC=10.0.0.67 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xA0 TTL=1 ID=3006 PROTO=2 
[ 2764.904767] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:c4:01:7c:0d:62:00:08:00 SRC=10.0.0.67 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xA0 TTL=1 ID=52216 PROTO=2 
crougeau@christian-NB205:~$ 




```

---

