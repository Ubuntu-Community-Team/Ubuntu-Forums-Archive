---
title: "Where, oh where, did my CD drive go?"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by Old *ix Geek on 2007-11-29
I have no idea what, or when it, happened, but I've lost my CD drive on my laptop. Somehow, **/media/cdrom0** became a regular directory, so when I [thought I] was happily copying files to a CD-RW...they were actually going into a directory named **/media/cdrom0**.  NOTE that I am using Feisty, not Gutsy (I've read about lost CD drives on Gutsy due to some bug, but that's not what I'm using).

My **/etc/fstab** hasn't changed; here's the pertinent line:
```
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

To make things even stranger, last night, issuing the following DID restore the drive:
```
mount -t iso9660 /dev/hda /media/cdrom0
```
but this morning the same command yields:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

**dmesg | tail -30** yields:
```
[ 4213.720000] hda: rw=0, want=68, limit=4
[ 4213.720000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[ 4266.240000] attempt to access beyond end of device
[ 4266.240000] hda: rw=0, want=68, limit=4
[ 4266.240000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[ 4299.776000] attempt to access beyond end of device
[ 4299.776000] hda: rw=0, want=68, limit=4
[ 4299.776000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[ 4433.404000] attempt to access beyond end of device
[ 4433.404000] hda: rw=0, want=68, limit=4
[ 4433.404000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[ 4617.832000] attempt to access beyond end of device
[ 4617.832000] hda: rw=0, want=68, limit=4
[ 4617.832000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[ 7646.468000] SMB connection re-established (-5)
[ 7668.224000] cdrom: This disc doesn't have any tracks I recognize!
[ 7911.036000] hda_intel: azx_get_response timeout, switching to polling mode...
[40377.244000] attempt to access beyond end of device
[40377.244000] hda: rw=0, want=68, limit=4
[40377.248000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[40419.544000] attempt to access beyond end of device
[40419.544000] hda: rw=0, want=68, limit=4
[40419.544000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[40724.168000] attempt to access beyond end of device
[40724.168000] hda: rw=0, want=68, limit=4
[40724.168000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[40832.148000] attempt to access beyond end of device
[40832.148000] hda: rw=0, want=68, limit=4
[40832.148000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[41440.192000] SMB connection re-established (-5)
```

Um...what the hell happened?  FWIW, the drive is a DVD/CD-RW combination, and when I put a CD in it, its light flashes as normal but that's it.

---

### Post by linuxonbute on 2007-11-29
> **Old *ix Geek said:**
> 
To make things even stranger, last night, issuing the following DID restore the drive:
```
mount -t iso9660 /dev/hda /media/cdrom0
```
but this morning the same command yields:

```
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


Dumb question I guess but 
Did you have a CD/DVD int the drive both times or was it only last night?

---

### Post by Old *ix Geek on 2007-11-29
That's not a dumb question. :)  Yes, I did have a CD in each time.

---

