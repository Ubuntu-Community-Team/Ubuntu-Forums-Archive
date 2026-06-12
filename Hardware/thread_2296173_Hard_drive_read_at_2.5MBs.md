---
title: "Hard drive read at 2.5MB/s"
date: 2015-09-23
forum: Hardware
---

### Post by yunchiluo on 2015-09-23
I have a headless media server that I’ve been using for several years now. It’s been entirely reliable, but some time ago 2 of the 4 hard drives started running very slowly.

The two slow functioning hard drives are connected to an SIL3124 RAID adapter. The two fast ones are connected directly to the motherboard. All 4 are different hard drives, WD, Samsung, and Toshiba, two 2TB and two 3TB. The drives are not running in a RAID array. I’m using SnapRAID.

While I’d like to point fingers at the RAID/JBOD adapter, the read/write speeds are at 100MB/s just after boot and for as long as I’m using it. It’s only after I let the drives idle for some period of time—and I don't know how long—that the speed drops and I need to reboot again to make it fast.

I wonder if the drives are stuck in some kind of weird mode after spin down but don't know how to test. smartctl says that my all of my drives are fine. Does anyone know what the problem might be or how to debug this issue?

hdparm output below:

```
> sudo hdparm -Tt /dev/sdf1

/dev/sdf1:
 Timing cached reads:   6032 MB in  2.00 seconds = 3016.41 MB/sec
 Timing buffered disk reads:  10 MB in  3.72 seconds =   2.69 MB/sec

> sudo hdparm -Tt /dev/sde1

/dev/sde1:
 Timing cached reads:   5592 MB in  2.00 seconds = 2796.49 MB/sec
 Timing buffered disk reads:   8 MB in  3.41 seconds =   2.34 MB/sec

> sudo hdparm -Tt /dev/sdd1

/dev/sdd1:
 Timing cached reads:   8212 MB in  2.00 seconds = 4107.42 MB/sec
 Timing buffered disk reads: 338 MB in  3.01 seconds = 112.40 MB/sec

> sudo hdparm -Tt /dev/sdc1

/dev/sdc1:
 Timing cached reads:   8374 MB in  2.00 seconds = 4188.83 MB/sec
 Timing buffered disk reads: 536 MB in  3.01 seconds = 178.30 MB/sec
```
I have them set to spin down after 2 hours using /etc/hdparm.conf

```
/dev/sdc {
  spindown_time = 244
}

/dev/sdd {
  spindown_time = 244
}

/dev/sde {
  spindown_time = 244
}

/dev/sdf {
  spindown_time = 244
}
```

df -i output

```
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda1         610800 482095    128705   79% /
udev              484830    558    484272    1% /dev
tmpfs             487028     14    487014    1% /tmp
tmpfs             487028    491    486537    1% /run
none              487028      3    487025    1% /run/lock
none              487028      2    487026    1% /run/shm
tmpfs             487028      1    487027    1% /var/log/apt
none              487028     14    487014    1% /var/cache/apt
/dev/sda2         610800 141230    469570   24% /home
/dev/sdc1         715424     14    715410    1% /mnt/toshiba-3tb-1
/dev/sdd1      122101760   2044 122099716    1% /mnt/wd-2tb-1
/dev/sdf1      183148544 131929 183016615    1% /mnt/wd-3tb-1
/dev/sde1      122101760   3935 122097825    1% /mnt/samsung-2tb-2
```

---

