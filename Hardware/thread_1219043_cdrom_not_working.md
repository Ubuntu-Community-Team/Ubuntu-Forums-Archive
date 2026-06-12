---
title: "cdrom not working"
date: 2009-07-21
forum: Hardware
---

### Post by Asrai99 on 2009-07-21
I was watching a DVD on my laptop today and it worked absolutely fine. After that I inserted a CD which couldn't be read. I didn't think anything of it at the time, since my laptop was busy crashing anyway (I think it overheated.) 

Anyway, now the drive won't play CDs or DVDs; in fact, several applications tell me that my laptop does not, in fact, have a CD drive. /etc/fstab |grep cdrom tells me this:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Mounting the drive doesn't work:

special device /dev/scd0 does not exist

I then tried lshw -class disk to see whether the drive is there, but all I got was this:

  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54161
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SBDO
       serial: SB2541H6GTRRNE
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=3011a9df

Now I'm a bit at a loss. Of course it's possible that my drive got fried when the computer crashed, but since it wouldn't read the CD beforehand I'm not so sure about that. Are there any other ways for me to check whether it's my system messing up somehow or whether it's the actual drive that's broken?

Any help would be appreciated!

---

