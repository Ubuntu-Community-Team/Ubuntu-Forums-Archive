---
title: "Maverick Constant Disk Access"
date: 2011-01-31
forum: Hardware
---

### Post by vortmax on 2011-01-31
I'm having an issue with Maverick on my laptop.  When the system is completely idle, I can watch the hard drive light flicker every 2 seconds (roughly).  It's a very consistent pattern.

Using atop, I've tracked the activity down to jdb2 and conky.  I found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607560") bug report that describes the issue as a kernel bug in 2.6.32, but I've upgraded to 2.6.35 (which is supposed to fix the bug) and the issue persists.

It seems when I shut down conky, the issue persists as well, but the write interval drops sharply.

So what in conky could be writing 8 to 12 kb of data to disk every 2 seconds?

---

### Post by NightwishFan on 2011-01-31
I think by default Ubuntu does not do much to power down the disks, which is good as it reduces disk life to be spun up and down all the time. I am not sure how to lower the write ratio or etc, but you can check the devices power management using this command. (Replace /dev/sda with your device name but it is probably /dev/sda) This command only "queries" the level of power management, you have to add a variable to set it, and it wont stick between reboots.

```
sudo hdparm -B /dev/sda
```

Explanation:
>        -B     Query/set Advanced Power Management feature, if the  drive  sup&#8208;
              ports  it.  A  low value means aggressive power management and a
              high value means better performance.   Possible  settings  range
              from  values  1 through 127 (which permit spin-down), and values
              128 through 254 (which do not permit  spin-down).   The  highest
              degree  of power management is attained with a setting of 1, and
              the highest I/O performance with a setting of 254.  A  value  of
              255 tells hdparm to disable Advanced Power Management altogether
              on the drive (not all drives support disabling it, but most do).

---

