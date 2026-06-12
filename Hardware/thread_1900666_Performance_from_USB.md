---
title: "Performance from USB"
date: 2011-12-26
forum: Hardware
---

### Post by Zahne on 2011-12-26
Hi, I'm thinking of running Ubuntu from a 32GB USB 2.0 flash drive. 

I was thinking this might be a good non-HDD alternative but I'm wondering, what's the performance like? I'm having a hard time finding comments on user experience running Ubuntu Desktop from a flash drive. I'm getting too many results that discuss how install Ubuntu via USB, which is not what I'm trying to do. 

So I'd love some feedback. 

Bottom line. I don't suppose it is as good or better than an SSD, but is it at least as good as an HDD?

---

### Post by mikewhatever on 2011-12-26
The performance is about the same, since the hardware is the same, save for the HDD, and most of the stuff runs from RAM. Disk access times are longer, which means significantly longer boot times or programs loading when they have to be read from disk.

I remember trying to boot from USB once, and it took so long, I thought it was stuck, but it was up and running after a couple of minutes.

---

### Post by C.S.Cameron on 2011-12-26
I find the speed quite a bit slower than running from SATA HDD.
Check the spec's of your flash drive and you will find a good one has ~ 28MB/s Read; 10MB/s Write while a SATA drive ~600 Mbps.
This is due to limitations of USB2.
I also find that things will sometimes grey out and pause while using the internet.

I understand that there are ways to get Ubuntu to run in RAM which is much faster that running from a drive.

---

### Post by snowpine on 2011-12-26
My experience agrees with the posters above; much slower than internal HDD.

If you must run from USB for whatever reason then check out distros like SliTaz or Puppy that are designed for the task.

---

### Post by shovenose on 2011-12-26
Keep in mind that the flash storage chips used in USB flash drives have limited write cycles, so it will get worn fairly quickly and become unusable. They are meant to move around data, not be used as a boot drive.

---

### Post by snowpine on 2011-12-26
> **shovenose said:**
> Keep in mind that the flash storage chips used in USB flash drives have limited write cycles, so it will get worn fairly quickly and become unusable. They are meant to move around data, not be used as a boot drive.

My experience is otherwise; I have a cheap $10 flash drive I've been "distro hopping" with for 3+ years with no loss of data or degradation of (terrible) performance.

---

### Post by C.S.Cameron on 2011-12-27
> **shovenose said:**
> Keep in mind that the flash storage chips used in USB flash drives have limited write cycles, so it will get worn fairly quickly and become unusable. They are meant to move around data, not be used as a boot drive.

Snowpine and I agree again, a decent flash drive will last years when used to run Ubuntu.

---

### Post by snowpine on 2011-12-27
An addendum to the above, I've never had a flash drive wear out, but I've definitely suffered a couple of mechanical hard disk drive failures...

---

### Post by efflandt on 2011-12-29
I too have never had any flash fail (I use name brands), but have had and seen mechanical hd failures.

Some "rough" speed comparisons using:
**sudo hdparm -tT /dev/sd**x# (x = sd letter, # = partition number)

```
Intel 80GB SSD Sata2 (64-bit 11.10)
/dev/sdb1:
 Timing cached reads:   10784 MB in  2.00 seconds = 5394.07 MB/sec
 Timing buffered disk reads: 742 MB in  3.00 seconds = 246.99 MB/sec

Seagate 1TB Sata2 HD
/dev/sda1: (Dell Utility)
 Timing cached reads:   9958 MB in  2.00 seconds = 4980.76 MB/sec
 Timing buffered disk reads:  38 MB in  0.31 seconds = 124.29 MB/sec

/dev/sda4: (64-bit 10.10)
 Timing cached reads:   10304 MB in  2.00 seconds = 5153.90 MB/sec
 Timing buffered disk reads: 232 MB in  3.02 seconds =  76.72 MB/sec

WD 500GB Passport HD on USB 2.0 (64-bit 10.10)
/dev/sdg1:
 Timing cached reads:   9770 MB in  2.00 seconds = 4886.63 MB/sec
 Timing buffered disk reads: 100 MB in  3.06 seconds =  32.73 MB/sec
(5400 rpm Sata1 HD on old laptop was not much faster)

Sandisk 16GB Class 10 SD on internal USB 2.0 (64-bit 11.10)
/dev/sdc1:
 Timing cached reads:   9574 MB in  2.00 seconds = 4788.59 MB/sec
 Timing buffered disk reads:  56 MB in  3.02 seconds =  18.54 MB/sec

PNY 4GB USB 2.0 stick (64-bit 11.10 iso)
/dev/sdg1:
 Timing cached reads:   9430 MB in  2.00 seconds = 4716.92 MB/sec
 Timing buffered disk reads:  70 MB in  3.05 seconds =  22.95 MB/sec
```Note that reading from cache does not vary that much, just initial read.

I just got the 16GB SD to boot 64-bit 11.10 on an Acer W500P tablet PC, but hdparm shows lower figures on that (AMD C-50 dual core 1 GHz w/HD 6250 video).  It can only boot alternative devices (to Win7 Pro on its 32GB SSD) when its included keyboard dock is attached.  No speed demon, but everything seems to work in Linux including its touch screen.

---

### Post by Moozillaaa on 2011-12-29
Disk [device] enumeration changes in some machines when stuff is plugged into USB ports, depending on MANY different factors.

---

