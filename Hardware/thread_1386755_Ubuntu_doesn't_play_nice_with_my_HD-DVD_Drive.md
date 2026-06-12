---
title: "Ubuntu doesn't play nice with my HD-DVD Drive"
date: 2010-01-21
forum: Hardware
---

### Post by humphreybc on 2010-01-21
I have a Toshiba laptop that has an HD-DVD drive. I just want to play regular DVDs, I know HD-DVDs are a dead format blah blah.

When I boot without anything in the drive, there is no listing under Places for my optical drive. But when I click "Computer" it does show me "CD/DVD Drive."

I right click and show properties, see attached. When I insert a CD, nothing happens. I can double click on the "CD/DVD Drive" for all time, and still nothing happens.

**However,** if I leave that disc IN the drive and reboot, then Ubuntu will pick up the optical drive and the disc fine, and it will run in VLC and I can watch my movie.

I have no idea where to start when troubleshooting optical drives. My fstab entry for the optical drive is:

```

# Optical Drive
/dev/scd0       		/media/cdrom0   		udf,iso9660 		user,noauto,exec,utf8 		0       0

```

Some more information, ran this when the Computer was running and I put a disc in:

```

benjamin@benjamin-laptop:~$ dmesg | grep -i cd | grep -i rom
[    0.981588] scsi 3:0:0:0: CD-ROM            TOSHIBA  DVDW/HD TS-L802A TO33 PQ: 0 ANSI: 5
[    0.983612] Uniform CD-ROM driver Revision: 3.20
[    0.983689] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   21.267584] cdrom: This disc doesn't have any tracks I recognize!
benjamin@benjamin-laptop:~$ 
benjamin@benjamin-laptop:~$ Read more: http://www.brighthub.com/computing/linux/articles/40346.aspx#ixzz0dEKurMAe

```

---

