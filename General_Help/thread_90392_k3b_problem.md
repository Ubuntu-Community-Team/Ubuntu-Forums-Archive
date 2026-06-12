---
title: "k3b problem"
date: 2005-11-14
forum: General Help
---

### Post by Brando569 on 2005-11-14
ive been having this sort of problem for quite some time and dont know how to fix it. im trying to burn a lot of data to DVD-Rs because i think my HDD is going to die soon (maxtor makes crappy harddrives, they last about a year or a lil more then die well atleast the diamond max +9 SATAs do). so i burn the 4.4gb of data (that also confused me, what happens to the other .3gb worth of space? the filesystem info doesnt take up that much does it?) and hit verify written data and it all comes back positive. when i go to mount the cd it wont let me. this is the error i get:

```

(both dvd drives fs types are set to auto in fstab)
brando@ra:~$ sudo mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

brando@ra:~$ dmesg | tail

attempt to access beyond end of device
hdc: rw=0, want=1028, limit=4
UDF-fs: No partition found (1)

attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
VFS: Can't find ext3 filesystem on dev hdc.

attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

```

these are the options im using in K3B v0.12.7:

Writing:
on the fly
verify written data

Settings:
No MultiSession

Filesystem:
Generate RockRidge Extensions
Generate Joliet extensions
Generate UDF Structures
Discard All Symlinks

Advanced:
Allow 103 character Joliet filenames
Allow 32 character iso9660 filenames
ISO level 2

whats wrong here?   :confused:

---

### Post by Brando569 on 2005-11-14
found my problem, it seems that you cant write dvds on the fly :-/

---

