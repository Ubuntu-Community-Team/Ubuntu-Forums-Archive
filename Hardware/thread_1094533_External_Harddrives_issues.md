---
title: "External Harddrives issues"
date: 2009-03-12
forum: Hardware
---

### Post by ChessPlayer2486 on 2009-03-12
Hello all.  Absolutely new to linux but I'm starting to wear out of Windows so I'm giving it a shot.  With that said, I am a Linux dummy so the lingo might be lost on me if you don't explain it to thoroughly.  If I have time I'll go borrow 'Linux for Dummies', might be good reading material.  Anyway, I've ranted on now, my problem that I have right now pertains to one Seagate 750gigabyte External with firewire connection and one WD Passport 250gigabyte External.  Both cannot be mounted onto Linux Gnome and I was trying to figure it out.  Unfortunately, Windows has turned me into a drooling braindead idiot that expects the platform to answer all his questions so I have no idea where to go from there.  Many thanks to the people helping me.  Also I'm using 64bit so I hope I didn't place this in the wrong section, if I did please move it to the right one, administrators, Thanks.

---

### Post by taurus on 2009-03-12
Make sure both connect and on.  Then, open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
dmesg | tail
sudo fdisk -l
df -h
```

---

### Post by ChessPlayer2486 on 2009-03-12
Thanks for the help, they both show now, but still gives me the error of not being mounted.

---

### Post by taurus on 2009-03-12
You can try to mount them by hand from a terminal.  What's the output of this command then.

```
sudo fdisk -l
```

---

### Post by ChessPlayer2486 on 2009-03-12
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders
Units = cylinders of 516 * 512 = 264192 bytes
Disk identifier: 0xea7ca61e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      208876    53890006    7  HPFS/NTFS
/dev/sda2          208877      605778   102400716    5  Extended
/dev/sda5          208877      216446     1953058   82  Linux swap / Solaris
/dev/sda6          603841      605778      500002   83  Linux
/dev/sda7          216447      254297     9765556   83  Linux
/dev/sda8          254298      603838    90181576   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS


This is the response I recieved before it sending me back to the original command line.

---

### Post by taurus on 2009-03-12
So you want to mount both /dev/sdb1 & /dev/sdc1.

```
sudo mkdir /media/sdb1 /media/sdc1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
df -h
```

---

### Post by ChessPlayer2486 on 2009-03-12
Thanks so much, I got my Western Digital to work but it gives me an error message for my firewire Seagate.  I had to force both but only WD worked it out.

> fuse: failed to access mountpoint /media/sdb1: No such file or directory


---

### Post by taurus on 2009-03-12
Did you remember to create that mount point before you mounted to it?

```
ls -la /media
```

---

### Post by ChessPlayer2486 on 2009-03-12
Just got it to work, hats off(props, if you're from NYC) to you.  Thanks for all the help.  This website is going on my favorites.  This'll help the pain from the popping of my linux cherry easier to bear.  :P

---

