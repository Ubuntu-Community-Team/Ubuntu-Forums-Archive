---
title: "Can't read Intel &quot;Fake RAID&quot; Striped"
date: 2009-01-17
forum: Hardware
---

### Post by locky28 on 2009-01-17
Hi all,

I've had a problem for a while where my ubuntu install can't read the two striped drives that Windows is installed on. Ultimately, I would like GRUB that is installed on the Ubuntu drive to be able to boot Windows but baby steps first.

These are the 4 drives listed in GParted:

/dev/sda   ---------___ sda and sdb are both Part of the RAID 0 NTFS
/dev/sdb   ---------
/dev/sdc   -------------This is my 1TB Storage Drive NTFS
/dev/sdd   -------------This is the 80GB drive Ubuntu is installed on


So first I'll show you what happens when I try to put it together with mdadm

```
locky@locky0:~$ sudo mdadm --assemble --scan
locky@locky0:~$ sudo mount -t ntfs-3g /dev/md0 /media/RAID
NTFS signature is missing.
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
locky@locky0:~$ 

```

Note that I've checked that /dev/md0 was then and I've created /media/RAID previously. From what I've read up, mdadm creates md0 and tries to map the array to that. Also I've run a chkdsk on the Windows array. Anyone know whats going on here?


Next up my attempt with dmraid.

```
locky@locky0:~$ sudo dmraid -s
ERROR: isw device for volume "Stripe" broken on /dev/sdb in RAID set "isw_eagajjhjaj_Stripe"
ERROR: isw: wrong # of devices in RAID set "isw_eagajjhjaj_Stripe" [1/2] on /dev/sdb
ERROR: isw device for volume "Stripe" broken on /dev/sda in RAID set "isw_bcbbeichjb_Stripe"
ERROR: isw: wrong # of devices in RAID set "isw_bcbbeichjb_Stripe" [1/2] on /dev/sda
*** Group superset isw_eagajjhjaj
--> Subset
name   : isw_eagajjhjaj_Stripe
size   : 976768256
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0
*** Group superset isw_bcbbeichjb
--> Subset
name   : isw_bcbbeichjb_Stripe
size   : 976766208
stride : 256
type   : stripe
status : broken
subsets: 0
devs   : 1
spares : 0
locky@locky0:~$ 

```

My first concern is the status being listed as broken, anyone know what that means?

```
locky@locky0:~$ sudo dmraid -r
/dev/sdb: isw, "isw_eagajjhjaj", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_bcbbeichjb", GROUP, ok, 976773166 sectors, data@ 0

locky@locky0:~$ sudo dmraid --activate y
ERROR: isw device for volume "Stripe" broken on /dev/sdb in RAID set "isw_eagajjhjaj_Stripe"
ERROR: isw: wrong # of devices in RAID set "isw_eagajjhjaj_Stripe" [1/2] on /dev/sdb
ERROR: isw device for volume "Stripe" broken on /dev/sda in RAID set "isw_bcbbeichjb_Stripe"
ERROR: isw: wrong # of devices in RAID set "isw_bcbbeichjb_Stripe" [1/2] on /dev/sda

```

Can anyone help out? I'm really lost with this one..... nfi atm

---

### Post by spartan777 on 2009-04-30
i don't have the same errors, but I also want to know how to read from a fakeraid array.

---

