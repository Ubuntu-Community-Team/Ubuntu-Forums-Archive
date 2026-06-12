---
title: "Dell Studio 1750 laptop rejects / ejects all CDs"
date: 2008-10-14
forum: Hardware
---

### Post by Sethleben on 2008-10-14
I'm running Hardy, 64bit, kernel 2.6.24-19-generic 

CD drive works perfectly in Vista (it is a dual booting machine). If I leave the CD in and boot to Linux, I can mount the CD ok. I can also eject without problems in Linux. However, when I try and reinsert the disc whilst running Linux, it is immediately ejected. This happens with any kind of CD. 

Hard to see how it could be a hardware issue, since the drive works fine in Windows. The drive is the type that consists of just a slot rather than an ejectable tray. 

Anyone have any ideas? 

A few similar problems seem to have been reported, but the only responses suggested were faulty hardware, or bad MP3 player software, neither of which explains my problem.

---

### Post by cariboo on 2008-10-14
What is the output of demsg when you insert a CD, that will give you a clue as to what is happening. In a terminal type:

```
dmesg
```

or got to System-->Aministration-->System Log-->File-->Open-->File SYstem-->/var/log/dmesg

Which ever you find easier.

Jim

---

### Post by Sethleben on 2008-10-14
dmesg gives the following suspicious entries:

```
[29637.674564] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[29676.897818] CPU0: Temperature/speed normal
[29676.897831] CPU1: Temperature/speed normal
[29698.984660] gvfsd-cdda[24660]: segfault at 7fd5ffffff82 rip 7f8fa3ff8306 rsp 4252cd80 error 4

```

---

### Post by Sethleben on 2008-10-14
But actually after checking a few times, these lines don't appear when I reinsert the CD. They seem to have been one-off error occurrences...

The repeated ejection of the CD doesn't leave any trail as detected by dmesg. Nevertheless, there is obviously some error registered here.

---

### Post by Sethleben on 2008-10-14
For your information, startup adds the following to the dmesg log regarding the CD drive:
```
[   19.056014] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-7 01.0 PQ: 0 ANSI: 5
[   19.056999] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D300 PQ: 0 ANSI: 5
[   19.160172] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.160191] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   19.162036] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.162081] sr 1:0:0:0: Attached scsi CD-ROM sr0

```

---

### Post by xENO_ on 2008-10-14
Do you remove the CD completely when you re-insert it? I have an issue on my Studio 1535 on Vista in which the CD will eject sometimes when I first log in (apparently at random), and then it will reject the CD until I completely remove the disc from the slot, wait a second or two and then put it back in.

---

### Post by Sethleben on 2008-10-15
> **xENO_ said:**
> Do you remove the CD completely when you re-insert it? I have an issue on my Studio 1535 on Vista in which the CD will eject sometimes when I first log in (apparently at random), and then it will reject the CD until I completely remove the disc from the slot, wait a second or two and then put it back in.

Yes, whether I remove it completely or not, or even if I try and force it to stay in (!), it makes no difference...

---

