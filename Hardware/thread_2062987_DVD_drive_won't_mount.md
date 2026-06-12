---
title: "DVD drive won't mount"
date: 2012-09-26
forum: Hardware
---

### Post by carranty on 2012-09-26
Hi, 

I'm running 12,04, 64bit and have a software CD from my university with a linux version of a program called maple that I'd like to install.  However my DVD drive does not appear to be mounted

```
carranty@Carranty-Desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc6       111G   31G   74G  30% /
udev            993M  4.0K  993M   1% /dev
tmpfs           401M  936K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  152K 1001M   1% /run/shm
/dev/sdb1       459G   48G  389G  11% /media/InternalStorage
```My computer recognises it has a DVD drive

```
carranty@Carranty-Desktop:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg0'    rwrw-- : 'SONY' 'DVD RW AW-G170A'
-------------------------------------------------------------------------
carranty@Carranty-Desktop:~$  sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AW-G170A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.71
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready

```I just can't seem to mount it. 

```
carranty@Carranty-Desktop:~$ sudo mount /dev/sg0 /media/CD
mount: /dev/sg0 is not a block device
```Any ideas?

---

### Post by BicyclerBoy on 2012-09-26
sr0 not sg0...

# this prob already exists..
mkdir /media/cdrom
mount -t iso9660 -o ro /dev/sr0 /media/cdrom

---

### Post by carranty on 2012-09-27
> **BicyclerBoy said:**
> sr0 not sg0...

# this prob already exists..
mkdir /media/cdrom
mount -t iso9660 -o ro /dev/sr0 /media/cdrom

Hi, thanks for replying, sorry about the delay.

Unfortunately the above didn't work

```
carranty@Carranty-Desktop:~$ sudo mount -t iso9660 -o ro /dev/sr0 /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I tired dmesg | tail as suggested, immediately after
```
carranty@Carranty-Desktop:~$ dmesg | tail
[   39.824021] wlan1: no IPv6 routers present
[  221.881976] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  262.745657] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  267.483214] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  287.586944] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  299.250781] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  358.944018] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  366.310761] hfs: can't find a HFS filesystem on dev sr0.
[  401.898596] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  454.714790] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```I tried the same command replacing /dev/sr0 with each of /dev/sg0, cdrom, cdrw, dvd,dvdrw in turn but the same thing happened for each.

I should also add that the DVD drive is definitely working, I just installed 12.04 a few weeks ago using it.  In fact, it automounts when I put a music cd in
```
carranty@Carranty-Desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc6       111G   31G   74G  30% /
udev            993M  4.0K  993M   1% /dev
tmpfs           401M  936K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  152K 1001M   1% /run/shm
/dev/sdb1       459G   48G  389G  11% /media/InternalStorage
**/dev/sr0        461M  461M     0 100% /media/ALANIS_MORISSETTE**
```or a film DVD

```
carranty@Carranty-Desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc6       111G   31G   74G  30% /
udev            993M  4.0K  993M   1% /dev
tmpfs           401M  936K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  152K 1001M   1% /run/shm
/dev/sdb1       459G   48G  389G  11% /media/InternalStorage
**/dev/sr0        6.7G  6.7G     0 100% /media/0784772**
```It just seems to be this disk.

Edit : This disk, by the way, is a genuine software cd from my university library, it contains Maple (an algebraic manipulation program) for windows/mac and linux systems.

---

### Post by agillator on 2012-09-27
My guess is the cd is bad since others mount without problem and the error message seems to indicate a bad block. This is easy to check, see if it is readable on someone else's computer. The fact that it is from your school's library actually makes it more likely that it is a problem with the cd (a scratch, etc). It has probably been used numerous times by numerous people some of whom did not care for it properly. You can try cleaning it or repairing it, but why go to the trouble? If it doesn't mount on another computer then take it back to the library, report that it is bad and get another. If it DOES mount on another computer, let us know.

P.S. How old is your drive? Has it led a rough life? Could it possibly be somewhat misaligned so it is not positioning the heads perfectly? Does this happen with any other cd or dvd? It is rare, but has happened to me before. If it is slightly misaligned and the drive creating the cd is slightly misaligned . . . . The odds are low but might be an explanation if it loads elsewhere or if the drive mounts some disks but not others.

---

### Post by BicyclerBoy on 2012-09-27
The LED lasers in optical drives age pretty badly.
Try polishing the disk.
Get the local video rental shop to polish it.

You could try:

ddrescue -d -b 2048 /dev/sr0 Maple.iso Maple.log

but I doubt it will work ..

---

