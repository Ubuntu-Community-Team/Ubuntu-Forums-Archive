---
title: "CDROM disappeared"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by talionis on 2006-06-07
I can't find this problem anywhere else, so I apologize if this posting is superfluous.

I've been running Dapper for a few weeks now, and it's gone largely without incident.  Two nights ago, I burned a couple of files to a CD, again without issue.  Today, however, I put a CD in the CDRW/DVDRW drive and it spins up, but then nothing happens.  I go to the media/cdrom and cdrom0 folders, and nothing's there.  When I put in ls /dev/hd*, hdc (the optical drive) didn't even show up.  It's completely gone, and now I can't access the disc , or even eject it.  Nothing I do will bring it back.  It worked fine two nights ago, and then poof.   /etc/fstab just has the typical entry.

The entry in /etc/fstab reads thusly:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

So yeah, /dev/hdc just went away, and I have no clue why.  Any ideas?

---

### Post by givré on 2006-06-07
okay, okay,
Try to be sure if it is mount or not (if you can't eject the disc, it's probably mount, but badly), run ```
more /etc/mtab
```
It should show you the filesystem actually mount.
If it is mount, try ```
sudo umount /dev/hdc
```
eject your cd and retry.

---

### Post by talionis on 2006-06-07
Thanks for the quick reply.  Funnily enough, minutes after your reply, I was able to eject the CD, but the drive itself remains essentially unseen by the OS.

```

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
varrun /var/run tmpfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/hda3 /storage ext3 rw 0 0

```

Unmount and mount do not work, since /dev/hdc is simply gone.  As such, they just return with hdc not found errors.

For what it's worth, the fstab reads as follows:

```

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /storage        ext3    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by givré on 2006-06-07
Strange problem.
Try to restart udev :
```
sudo /etc/init.d/udev restart
```
If it not work, go for a reboot

---

### Post by talionis on 2006-06-07
No go, unfortunately, and I've already rebooted several times after looking at various things.

---

### Post by givré on 2006-06-07
It is more and more mysterious. What do you have if you do
```
 dmesg |grep hdc
```

---

### Post by talionis on 2006-06-07
```

[4294674.594000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:pio, hdd:pio

```

---

### Post by Fornie on 2006-06-07
:confused: whaaa i got similar problem...

(1) i played audio cd without a problem last sunday but when i tried to play VCD on it yesterday (tried opening the VCD using mplayer) it just freeze up on me nothing happens on the computer but i see the cdrom light lit up as if reading the disk...
(2) i tried to eject the disk but it won't...
(3) tried sudo umount /dev/hdc but its giving me error message...
(4) so i inserted a paper clip on the cdrom hole to manually open the cdrom door (i know, not a good idea!)...
but now won't eject from OS / pressing the eject button...
(5) tried restarting the system several times (even boot in BIOS to check if eject button will work) but to no avail...

now my cdrom drive wo'nt lit up anymore...what seems to be the problem? please help! thanks ](*,)

---

### Post by talionis on 2006-06-08
I just noticed that if I get the drive open and shut it, something pops over my speakers, and my multimedia keys stop changing my volume unless I rerun xbindkeys-config (which I had to use to bind them so I could change the PCM volume, a problem that really needs fixed).

---

