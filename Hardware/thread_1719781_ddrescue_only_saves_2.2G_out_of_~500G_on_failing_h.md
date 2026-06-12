---
title: "ddrescue only saves 2.2G out of ~500G on failing hdd... how can I save the rest?"
date: 2011-04-02
forum: Hardware
---

### Post by yossarian42 on 2011-04-02
So my 1Tb drive decided to disappear while I was using it. I used the manufacturer's own tools (seagate's seatools) which merely told me that it's about dead. I'm currently running ubuntu off a liveCD. I checked the SMART status, which is "imminent failure": the reallocated sector count is 2062, which I'm guessing is pretty bad.

Being an idiot, I don't have a backup of that drive, so I attempted to use ddrescue to save my data. It has managed to get 2.2G off the drive, but it just skips the rest. This is the output:

```

Initial status (read from logfile)
rescued:     2326 MB,  errsize:    997 GB,  errors:       1
Current status
rescued:     2326 MB,  errsize:    997 GB,  current rate:        0 B/s
   ipos:     2977 MB,   errors:       1,    average rate:        0 B/s
   opos:     2977 MB,     time from last successful read:      22 m

```I've been through the steps here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), but that's as far as I got.

Would it be safe to mount the drive as read-only and just use cp? Or is that likely to make the drive catch fire? Any help would be very much appreciated!

---

