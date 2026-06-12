---
title: "Dell Inspiron 6400 - Slow SATA drive"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by spotenza on 2006-06-29
I just bought a new inspiron 6400 with an 80g 5400rpm SATA drive. It seems to be a bit slow launching programs such as firefox especially when compared to my older desktop. 

I ran an hdparm test and here is the output:
```

$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   3924 MB in  2.00 seconds = 1961.88 MB/sec
 Timing buffered disk reads:   96 MB in  3.05 seconds =  31.45 MB/sec

```

The buffered disk reads seems a bit slow... Any comparisions or ideas?

Here is the drive info:
```

$ sudo sdparm -i /dev/sda1
    /dev/sda1: ATA       TOSHIBA MK8032GS  AS11
Device identification VPD page:
  Addressed logical unit:
    id_type: vendor specific [0x0],  code_set: ASCII
 00     4c 69 6e 75 78 20 41 54  41 2d 53 43 53 49 20 73    Linux ATA-SCSI s
 10     69 6d 75 6c 61 74 6f 72                             imulator

```

And here is the SATA controller:
```

$ lspci | grep ATA
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)

```

---

### Post by Hellkeepa on 2006-06-30
HELLo!

If you're running on the -686 kernel, please try with the -386 kernel: There are a few bugs in the -686 one, one of which leads to poor CPU performance. This may be an side effect of that bug.

Happy codin'!

---

### Post by spotenza on 2006-06-30
Hellkeepa,

Thanks for the suggestion. I booted into the -386 kernel and I'm still getting similar performance:

```

steve@steve-laptop:~$ uname -a
Linux steve-laptop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
steve@steve-laptop:~$ sudo hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:   4168 MB in  2.00 seconds = 2083.87 MB/sec
 Timing buffered disk reads:   96 MB in  3.02 seconds =  31.83 MB/sec

```

---

### Post by Hellkeepa on 2006-07-01
HELLo!

Ah, sucks. Sorry I couldn't be of any assistance, hope you get it sorted out.

Happy codin'

---

### Post by m94mni on 2006-07-02
30 Mb/s is not exceptionally slow at all, especially not on a 5400rpm drive. Or are you experiencing slowness somewhere else than hdparm? If not, I wouldn't worry.

---

### Post by spotenza on 2006-07-12
m94mni: thanks for the response. I did some comparisons with some other drives and you're right, 30Mb/s isn't bad. I forgot that the drive in my older desktop is a 7200rpm drive and it definitely helps when launching programs.

---

