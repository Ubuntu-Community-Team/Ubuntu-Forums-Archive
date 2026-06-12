---
title: "DVD-R will not mount: &quot;No media found&quot; Error"
date: 2008-12-17
forum: Hardware
---

### Post by puzzlefreak on 2008-12-17
Hi,

I've been recently trying to burn a few DVD's and for some reason it automounts CD's, but it won't automount DVD's. I've tried mounting through the terminal, editing fstab, nothing has worked so far.

This is what comes up in /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=07fee7ee-afc3-4bbf-8677-20ce27809eee /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=bd9229e9-1fd5-43f6-b2a6-0dfb40b35d9b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Can anyone help me out?

---

### Post by puzzlefreak on 2008-12-18
Does anyone have any idea what it is?

---

### Post by puzzlefreak on 2008-12-18
Can someone please help me out?

---

### Post by puzzlefreak on 2008-12-20
Anyone?

---

### Post by Carl Hamlin on 2008-12-20
> **puzzlefreak said:**
> Hi,

I've been recently trying to burn a few DVD's and for some reason it automounts CD's, but it won't automount DVD's. I've tried mounting through the terminal, editing fstab, nothing has worked so far.

This is what comes up in /etc/fstab



Can anyone help me out?

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

What happens when you mount via the terminal?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNQUUACgkQyLm4ydrABvduawCfcHjnA1vfAHFyDPFcqvennH1a
iXYAnRXBsAuZSEpqgLik9nW3DSLE/FEl
=g9Sz
-----END PGP SIGNATURE-----

---

### Post by puzzlefreak on 2008-12-20
> sudo mount /media/cdrom0
sudo: unable to resolve host Eryk's Laptop
mount: No medium found


And also

> sudo mount /media/cdrom0 -o unhide
sudo: unable to resolve host Eryk's Laptop
mount: No medium found


Any idea?

---

### Post by puzzlefreak on 2008-12-20
It automounts commercial DVD's just fine, any ideas?

---

### Post by puzzlefreak on 2008-12-20
bump?

---

### Post by puzzlefreak on 2008-12-20
I can't be the only one having this problem, can I?

---

### Post by puzzlefreak on 2008-12-20
bump

---

### Post by puzzlefreak on 2008-12-20
I am an idiot, I have a DVD-ROM drive, so I can't burn DVD's anyway. Thanks for all the replies... :x

---

### Post by Sprax on 2009-01-21
You're not alone. I can burn CD-R:s fine but when I put a DVD in the burner (which, yes, can burn DVD:s) it doesn't detect them. Very annoying...

---

### Post by SSBal on 2009-07-30
Any ideas regarding this ?
I can burn DVD + R with ubuntu but DVD-R are not mounted.



~$ sudo mount /dev/dvd3 /mnt 
gave 
mount: /dev/sr0: unknown device

sudo lshw || less 
gave 
*-cdrom
                description: DVD reader
                product: DVD+RW SOHW-802S
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom3
                logical name: /dev/cdrw3
                logical name: /dev/dvd3
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UPP6
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc

Please help !!

---

