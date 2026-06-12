---
title: "Data transfers are like tortoise walk !! (slow)"
date: 2009-10-16
forum: Hardware
---

### Post by chinmaya_n on 2009-10-16
Hi

I observed data transfers on my system are very slow from the begining....!:confused:
Even from NTFS formated disk to a NTFS formated pen-drive is very slow (1Mb)...!:(
What is the exact problem?? What should i do to improve its speed!?!

---

### Post by Bucky Ball on 2009-10-16
What hardware are you using?

---

### Post by chinmaya_n on 2009-10-17
Mine is a desktop with gigabyte-G31 motherboard and C2D processor and Kingston 8GB pendrive!!

---

### Post by Bucky Ball on 2009-10-17
That would probably be it. No internal hard drive you're saying? If not, you're travelling at USB data transfer speed(s).

---

### Post by chinmaya_n on 2009-10-17
the usb-2.0  data-transfer speed is 480Mbps(60MBps) !! But i'm running at just 1MBps :confused: ??!!

---

### Post by chinmaya_n on 2009-10-18
Does any one know what is the problem ??
Does any one facing the same problem ??

---

### Post by darco on 2009-10-18
are you running an x64 bit OS? If so, you may want to head over to x64 forum and search on this ongoing issue


darco

---

### Post by chinmaya_n on 2009-10-19
> are you running an x64 bit OS? NO ........ i'm not using X64 ! Mine is i386

---

### Post by dabl on 2009-10-19
Not a new issue, unfortunately, and not limited to 64-bit systems:

[http://ubuntuforums.org/showthread.php?t=793688](http://ubuntuforums.org/showthread.php?t=793688)

---

### Post by Giblet5 on 2009-10-19
> **chinmaya_n said:**
> the usb-2.0  data-transfer speed is 480Mbps(60MBps) !! But i'm running at just 1MBps :confused: ??!!

480Mbps = 48MB/s, max theoretical. You'll never see half that in a terabyte-sized transfer.

Just sayin.

---

### Post by Giblet5 on 2009-10-19
It might also be useful to try all of the eternal USB jacks with your USB stick.

It's possible that one of them uses a physically different controller from the internal storage and that would provide a noticable improvement.

---

### Post by chinmaya_n on 2009-10-19
> It's possible that one of them uses a physically different controller from the internal storage and that would provide a noticable improvement.

For my desktop everything works same..... i only 've one usb2.0 port and 3 usb1.1 ports

---

### Post by chinmaya_n on 2009-10-19
> Not a new issue, unfortunately, and not limited to 64-bit systems:

[http://ubuntuforums.org/showthread.php?t=793688](http://ubuntuforums.org/showthread.php?t=793688)

The thread was so huge....!! 
Ofcource i'm reading it :)
If you have already read it and known any proper reason plz consolidate that and post here !!

---

### Post by chinmaya_n on 2009-10-19
I tried by editing the lines in the grub as suggested in this thread (* pci=routeirq*): [http://ubuntuforums.org/showthread.php?t=793688](http://ubuntuforums.org/showthread.php?t=793688) but it didnt work for me... may be they were using 8.04 but i'm using 9.04 !!

---

### Post by chinmaya_n on 2009-10-21
Can anyone tell me a fix for 9.04 ??

---

### Post by chinmaya_n on 2009-10-31
Yesterday i copied  6GB for a pendrive to my HDD transfer rate was 20+MB/sec....!
But the problem comes while copying from HDD to pendrive!

I tried to copy 40GB of data from one internal HDD to another internal HDD.... 
First i was delighted to see the transfer rate of 42MB/sec but gradually it is decreasing now..... now it is running at 21MB/sec...! don't know how much it is going to decrease !! 

Does anyone know a fix for 9.04(My system is completely updated) !

---

### Post by chinmaya_n on 2009-10-31
```
$ sudo hdparm -Tt /dev/sdb5

/dev/sdb5:
 Timing cached reads:   2622 MB in  2.00 seconds = 1311.68 MB/sec
 Timing buffered disk reads:  188 MB in  3.03 seconds =  62.03 MB/sec
``` Though it shows like this ..... ! My internal HDD to internal HDD are running at 36MB/sec!! from the output I think it should be around 50MB/sec !!
( I really dont know what that command is ! :( but saw in some other post )

---

### Post by chinmaya_n on 2009-10-31
> **Giblet5 said:**
> It might also be useful to try all of the eternal USB jacks with your USB stick.

It's possible that one of them uses a physically different controller from the internal storage and that would provide a noticable improvement.
All the ports are showing similar transfer rates !!
No use ! :(

---

