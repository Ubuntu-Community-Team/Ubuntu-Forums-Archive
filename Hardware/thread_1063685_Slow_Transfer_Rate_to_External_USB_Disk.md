---
title: "Slow Transfer Rate to External USB Disk"
date: 2009-02-08
forum: Hardware
---

### Post by Helios89 on 2009-02-08
Hi all,
Recently I had to transfer to my External HD quite a lot of GBs, but the transfer rate was very very slow (from around 2.5 MB/s to 3.2 MB/s)

I checked that the usb is recognized as 2.0.

I tried a fix i found somewhere in this forums (rmmod ehci_hcd && modprobe ehci-hcd) and it seemed to speed up it a little (once I arrived at 5 MB/s!) but now if I use this method, it doesn't work anymore.

Here's the result of hdparm to test my drive speed:

```
davide@hati:~$ sudo hdparm -Tt /dev/sdb1

/dev/sdb1:
 Timing cached reads:   2160 MB in  2.00 seconds = 1080.20 MB/sec
 Timing buffered disk reads:   96 MB in  3.00 seconds =  31.95 MB/sec
davide@hati:~$ 

```

I still use Ubuntu 8.04 (will go to 9.04 as soon as possible) and this is my uname -a:
```

Linux hati 2.6.24-23-generic #1 SMP Thu Feb 5 15:00:25 UTC 2009 i686 GNU/Linux
```

What should I do to achieve the highest (or just a higher) transfer speed to my USB disk? :neutral:

---

### Post by Helios89 on 2009-02-12
The transfer in the other direction seems to go faster (as expected) but with a 17 MB/s speed. :(

---

### Post by abdusamed on 2009-08-17
i** have the same problem on ubuntu 9.04**. The same usb on vista had a transfer rate of 30 to 25 mb per sec. On ubuntu, doing the same thing has much lower transfer rate, as mentioned,, around 3 or 4 mb/s. Any help..
copying data from pc to the stick

---

### Post by Arup on 2009-08-17
In BIOS disable legacy USB support and for hdds enable AHCI mode.

---

