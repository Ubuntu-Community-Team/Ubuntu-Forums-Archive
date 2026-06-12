---
title: "cannot mount DVD disc"
date: 2010-02-04
forum: Hardware
---

### Post by mc2718 on 2010-02-04
Hi,

Ever since I upgraded from good old Fedora 4 (!) a week ago to Ubuntu 9.04, I cannot use the CD/DVD drive in my laptop. Mounting any disc, as root, returns after a while with the error

  mount: no medium found on /dev/sr0

I tried this both with original DVD movie discs and CD games (mplayer cannot 'see' the DVD disc either). On the other hand Fedora 4 had no problem with any of these, moreover, my Windows XP (I have a dual-boot system) mounts and plays these discs just fine.

My suspicion is that the problem must be with the (kernel?) DVD driver on Ubuntu - or perhaps the device /dev/... creation. Anybody has an idea how to get things working again?

---------

This all is happening on a Sharp M4000 notebook. The DVD-related lines from /var/log/dmesg are

[    2.086078] scsi 0:0:0:0: CD-ROM            MATSHITA UJDA765 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    2.087014] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.087019] Uniform CD-ROM driver Revision: 3.20
[    2.087103] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.087148] sr 0:0:0:0: Attached scsi generic sg0 type 5

'lshw' shows the DVD drive as

           *-cdrom
                description: DVD reader
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd
                configuration: status=open

--------

I tried two ways to mount discs as root:

# mount /media/cdrom0/
mount: no medium found on /dev/sr0
  
# /mount /dev/sr0 /media/cdrom0
mount: /dev/sr0: unknown device

This latter is especially troubling. 'ls' reports

#dir /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 2010-02-01 21:05 /dev/sr0
#dir /dev/dvd
lrwxrwxrwx 1 root root 3 2010-02-02 02:05 /dev/dvd -> sr0
#dir /dev/cdrom
lrwxrwxrwx 1 root root 3 2010-02-02 02:05 /dev/cdrom -> sr0

[EOF]

---

### Post by Yellow Pasque on 2010-02-05
> ```
*-cdrom
description: DVD reader
physical id: 0
bus info: scsi@0:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
capabilities: audio cd-r cd-rw dvd
configuration: **status=open**
```

Was your drive actually open when you ran the command?

---

### Post by mc2718 on 2010-02-05
No, not at all... it had a disc inside.

EDIT: by the way, I just tested with drive open - 'lshw' reports the same status=open...

---

### Post by mc2718 on 2010-02-05
By the way, my Fedora kernel was 2.6.15-1.1834. Something must have happened to the CD/DVD driver between 2.6.15-1 and 2.6.28-17...

---

### Post by mc2718 on 2010-03-12
Strangely, this problem got cured mysteriously. Initially I was forced to use an external drive for DVDs. Then a few days ago even that stopped mounting. Unplugging/replugging numerous times did not help, but after a system reboot both external and internal CD/DVD drives started to work (this was around the 15th reboot since I posted this problem). 

I have absolutely no way telling whether this is permanently solved now, but I am hopeful. It must have been some quirk with hardware detection, I think.

---

### Post by bart.vanaudenhove on 2010-05-01
I had a somewhat similar problem on my HP Laptop, maybe it's related... On my computer any data cd or DVD would read  and write fine, but audio cds and movie dvds would not be recognized.

For me the solution was to physically slip the optical drive out of the  computer (unscrew a vise in the back and push the drive a bit out) =  unplugged and power off off course =, plug it back in, and at next  startup everything was fine. (I found it in another post somewhere)

From time to time the same problem reappears and the same solutions  works for a while...

This is in Ubuntu 9.10.

---

