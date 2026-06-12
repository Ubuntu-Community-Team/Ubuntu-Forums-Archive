---
title: "anyone using an SSD?  Please post a quick benchmark"
date: 2009-08-09
forum: Hardware
---

### Post by graysky on 2009-08-09
I'm considering an SSD for my Linux root and /home.  If you're using an SSD under Arch, can you please run a quick benchmark for me and post the results in this thread?  You can use hdparm to do a quick read test.  Here is an example using my HDD.

```
# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   14500 MB in  2.00 seconds = 7258.88 MB/sec
 Timing buffered disk reads:  368 MB in  3.01 seconds = 122.16 MB/sec
```

Beyond that, have you noticed any substantial speed ups over an HDD, like launching programs, booting the system, etc.

---

### Post by Jose Catre-Vandis on 2009-08-09
Not on Arch, but CLI Xubuntu on Acer Aspire One 8GB SSD
```
# sudo hdparm -Tt /dev/sda

/dev/sda
Timing cached reads:   1304 MB in  2.00 seconds = 651.70 MB/sec
 Timing buffered disk reads:  116 MB in  3.04 seconds = 38.13 MB/sec
```

much "slower" than your results, and giving about the same results as my PATA HDD on another machine !

---

### Post by hetx on 2009-08-09
/dev/sda:
 Timing cached reads:   14976 MB in  2.00 seconds = 7497.67 MB/sec
 Timing buffered disk reads:  336 MB in  3.04 seconds = 110.41 MB/sec

Ran it on Ubuntu in GNOME on a good old mechanical hard drive though.

Tried it on my EEE (with an SSD) but got the scary low 619MB/sec and 36.95MB/sec

---

### Post by markbuntu on 2009-08-09
SSDs are very very slow and still expensive. Unless you have some pressing need for high survivability you might want to reconsider. 

The current ones are definitely not faster than hdds. Newer technology is making its way into the pipeline that could remedy this but it is still at least a year away and initial pricing will be astronomical as usual. I am not expecting to see sdds that can compete with hdds on speed and price for at least 2 years and read/write life for another year or so after that.

Basically a SSD will be anywhere from 2-10 time slower than your average hdd and this will increase over the life of the drive. Due to the limited read/write cycle life of SSDs the caching scheme is very different since they must not let too many read writes occur and so use large caches and read and write seldom. They also must spread the read/writes across the drive to avoid premature failure by using the same area of the drive too often. All this takes time and processing power. 

linux format magazine has a netbook review that explains this. ( I am a old guy, I like to read real paper magazines).

---

