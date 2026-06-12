---
title: "DVD drive seems to read slow"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by swoll1980 on 2008-04-20
Is there a way to run a speed test on it to see if I'm getting the 52/20 X speeds I'm supposed to get

---

### Post by nicedude on 2008-04-21
This command tests my DVD speed with a disk in the drive, but your cd might not be scd0
Just type this in a terminal window to see if it will work for you.
sudo hdparm -tT /dev/scd0

My laptop results for a DVD 20x drive
nicedude@mybox:~$ sudo hdparm -tT /dev/scd0

/dev/scd0:
 Timing cached reads:   1852 MB in  2.00 seconds = 926.35 MB/sec
 Timing buffered disk reads:    8 MB in  3.69 seconds =   2.17 MB/sec

---

