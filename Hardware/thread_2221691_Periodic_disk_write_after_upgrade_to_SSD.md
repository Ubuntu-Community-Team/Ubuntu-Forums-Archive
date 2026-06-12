---
title: "Periodic disk write after upgrade to SSD"
date: 2014-05-03
forum: Hardware
---

### Post by jackyDon on 2014-05-03
I just migrated my (x)ubuntu installation form a hard drive to a SSD
I booted into a live-cd and rsync'ed the files to the ssd (excluding mnt, lost+found, sys and proc). Then I re-created the missing folders on the ssd

finally I updated the /etc/fstab
this is what it looks like right now:

```

UUID=... /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       1
UUID=... none            swap    sw              0       0


```
( both / and swap are on the SSD )

Everything seems to be working find now, the system boots fine (and fast)


But I just noticed that the drive is periodically writing something with 4MB/s and 8MB/s speed (constantly jumping from 4 to 8, and then back to 4 again - for ever)
At least that's what the System Load Indicator shows me - though the LED is also constantly blinking in a very periodic and "artificial" manner

I've also ran iotop, but it showed me nothing - it said that there is no disk writing going on at all

.....which is weird. There is enough RAM left, and the swap is also completely empty


There is also another strange thing going on (not sure if it's related)
But TRIM doesn't seem to be working....
I followed the instructions here: [https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](https://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
but I always keep seeing the deleted data (instead of the 0's that I'm supposed to see)

Does anybody know what might cause this strange behavior?

---

