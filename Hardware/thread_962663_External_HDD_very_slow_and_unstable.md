---
title: "External HDD very slow and unstable"
date: 2008-10-29
forum: Hardware
---

### Post by ACGarib on 2008-10-29
Hi, I have a seagate freeagent pro 500 GB external HDD connected to a Dell Vostro 1500 laptop via firewire and I get absolutely terrible performance for copying files from the external to my internal HDD, and copying files from my external to another folder in my external HDD. (around 90 KB/s) This happens for larger files over 50 MB or so. Small files transfer at a much higher speed of 11 MB/s. Going from my internal to the external is even better at 14 MB/s.

Doing a speed test via hdparm gives:

```
andrew@andrew-laptop:~$ sudo hdparm -tT /dev/sdb1

/dev/sdb1:
 Timing cached reads:     2 MB in 24.44 seconds =  83.80 kB/sec
 Timing buffered disk reads:    2 MB in 22.31 seconds =  91.78 kB/sec
```

Isn't the cached read supposed to be very high, like in the multiple GB/s range?



The other problem with this external HDD is its stability. When I transfer a chunk of files over 100 MB or so from the external to the internal HDD or from itself to itself, the file transfer window will usually freeze, nautilus will freeze, and the drive will start to make lots of very loud clicks. (about 50 clicks per second give or take, so it almost sounds like a buzz)

The same thing happens if I transfer files via the terminal:
```
cp -r /media/FreeAgent\ Drive/files /destination
```

From here on, I get errors whenever I try to access the disk. (input/output error). The only thing I can do is browse the files on the disk. Most of the files dissapear, leaving only the folders. Opening the remaining files will freeze whatever program tries to access the file. I can unmount the drive, but then I can't mount it again. The drive disappears and continues to click. The drive won't even turn off if I push the on/off button.

The only thing I can do is unplug the external HDD, then everything is back to before.


I've done some research, and it appears that all distributions of linux suffer from slow USB external HDD transfer speeds around 5 MB/s, but my drive is connected via firewire and the transfer speed is an abysmal .09 MB/s - plus my drive freezes.


Is there anything I can do to get my drive working properly?

Thanks,
Andrew

---

### Post by ACGarib on 2008-11-10
Well, things have been steadily getting worse. A reformat helped for a little bit, but it almost never works now. I tried booting into windows, installing the drivers and diagnostic tools, and the diagnostic test gives me an error of A7DDD46E, which means my drive is dead/dying.

Too bad this couldn't have happened earlier so I could return it to best buy instead of having to deal with seagate's return policy. Hopefully Seagate takes it back instead of replacing it with another piece of junk. (or even takes it back at all)

Anybody know of any good ubuntu compatible external hard drives? Seagate (or at least their freeagent pros) are out of the question due to their problems with ubuntu (and windows), mainly the sleep problem, the deathly slow transfer speed, and the esata problems.

I see a Lacie 301313U 500 GB esata/firewire/usb drive that has pretty good reviews. Anybody have any experience with this and it's linux compatibility?

---

