---
title: "natty don't detect an external hard disk"
date: 2011-08-01
forum: Hardware
---

### Post by juandadamo on 2011-08-01
Hello,
I've a problem regarding an external USB hard disk (Lacie Rugged 1 Tb, usb 3.0).
I was able to format it in a partition (sda1) of my laptop(dell vostro 1015) where I've Ubuntu maverick i386 installed. I've created two NTFS partitions (regretfully i need to copy data from windows).

 The problem is that when I reboot and use my natty 64b partition (sda5) I'm not able to even detect the disk. when I put 

lsusb
Bus 002 Device 004: ID 059f:104b LaCie, Ltd 

the system see an usb device but when i put sudo sfdisk -l, I'm just able to see my internal disk partitions (sda)

I tried "utility disk" and it does see the disk as /dev/sdb but with 0 capacity, non partitioned...

gparted doesn't list the volume

another issue is that if I've this usb disk connected, the system doesn t finish booting natty64.

I use maverick with this disk but if you have any ideas please help me.

many greetings

Juan

---

### Post by gir861 on 2011-08-01
Hi, did you tried your USB hdd on another machine?

---

### Post by juandadamo on 2011-08-01
> **gir861 said:**
> Hi, did you tried your USB hdd on another machine?

thanks for your answer and
yes, it works as I tried on windows or mac machines (not much ubuntu on this lab :(  )

---

### Post by coffeecat on 2011-08-01
Curious that Natty doesn't detect it, but Maverick does. Maverick and Natty are on different partitions on the same machine? Have I understood you correctly?

Boot into Natty, plug the drive in and switch it on, and then open a terminal and post the output of:

```
dmesg | tail
```

---

### Post by juandadamo on 2011-08-01
It is correct, I've two partitions Maverick(sda1) and Natty(sda5) that shares the same /home
So

```
dmesg | tail
[ 8538.351140] sd 7:0:0:0: [sdb] READ CAPACITY failed
[ 8538.351143] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 8538.351150] sd 7:0:0:0: [sdb] Sense not available.
[ 8538.351156] sd 7:0:0:0: rejecting I/O to offline device
[ 8538.351162] sd 7:0:0:0: [sdb] Write Protect is off
[ 8538.351167] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 8538.351172] sd 7:0:0:0: rejecting I/O to offline device
[ 8538.351178] sd 7:0:0:0: [sdb] Asking for cache data failed
[ 8538.351182] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 8538.351436] sd 7:0:0:0: [sdb] Attached SCSI disk
```

---

### Post by coffeecat on 2011-08-01
Well - Natty is detecting its presence and this:

```
[ 8538.351436] sd 7:0:0:0: [sdb] Attached SCSI disk
```

... suggests it ought to be seeing it as sdb, as in Maverick. Try running "sudo fdisk -lu" again after checking that you get that last line from dmesg.

---

### Post by juandadamo on 2011-08-01
So
```
dmesg | tail
[27641.311098] sd 8:0:0:0: [sdb] READ CAPACITY failed
[27641.311102] sd 8:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[27641.311108] sd 8:0:0:0: [sdb] Sense not available.
[27641.311114] sd 8:0:0:0: rejecting I/O to offline device
[27641.311125] sd 8:0:0:0: [sdb] Write Protect is off
[27641.311127] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
[27641.311136] sd 8:0:0:0: rejecting I/O to offline device
[27641.311139] sd 8:0:0:0: [sdb] Asking for cache data failed
[27641.311141] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[27641.311319] sd 8:0:0:0: [sdb] Attached SCSI disk
```
and then
```
 sudo fdisk -lu

Disk /dev/sda: 500 GB, 500105249280 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976768065 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1              63    78332939    39166438   83  Linux
/dev/sda2        78332940   820519874   371085435   83  Linux
/dev/sda3   *   820520960   911421439    45447885    7  HPFS/NTFS
Warning: Partition 3 does not end on cylinder boundary.
/dev/sda4       911423486   976773119    32676210    5  Extended
Warning: Partition 4 does not end on cylinder boundary.
/dev/sda5       911423488   972861439    30716280   83  Linux
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda6       972863488   976773119     1959930   82  Linux swap
Warning: Partition 6 does not end on cylinder boundary.
```

(thanks for helping !)

---

### Post by coffeecat on 2011-08-01
Hmm. Now I'm baffled. The output of dmesg days that sdb has been attached but fdisk doesn't see it. There are some problem lines in your output of dmesg which you don't normally see when plugging in a USB drive, but I'd assumed the last line meant that the device was attached OK. Obviously I was wrong.

Sorry - out of ideas.

---

### Post by juandadamo on 2011-08-06
just to post the output of fdisk on maverick(/dev/sda1) (where the disk works)

```
sudo fdisk -lu

Disque /dev/sda: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x000db549

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1              63    78332939    39166438+  83  Linux
/dev/sda2        78332940   820519874   371093467+  83  Linux
/dev/sda3   *   820520960   911421439    45450240    7  HPFS/NTFS
/dev/sda4       911423486   976773119    32674817    5  Etendue
/dev/sda5       911423488   972861439    30718976   83  Linux
/dev/sda6       972863488   976773119     1954816   82  Linux swap / Solaris

Disque /dev/sdb: 1000.2 Go, 1000204878336 octets
255 têtes, 63 secteurs/piste, 121601 cylindres, total 1953525153 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x6c910a94

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1              63  1023999164   511999551    7  HPFS/NTFS
/dev/sdb2      1023999165  1953520064   464760450    7  HPFS/NTFS
```

---

