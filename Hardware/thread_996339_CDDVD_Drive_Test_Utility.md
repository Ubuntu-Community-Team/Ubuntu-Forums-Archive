---
title: "CD/DVD Drive Test Utility?"
date: 2008-11-28
forum: Hardware
---

### Post by HDTimeshifter on 2008-11-28
Anybody know of a good Linux CD/DVD drive test utility?

Brasero takes forever to burn an audio CD to an image.  It slows to .1x and 6 hours+ to burn a CD to HD, then usually fails to burn to a disc.  I've successfully burned a couple of CDs out of a dozen or so I tried.  I want to test my CD drive to make sure it's not the drive itself.

---

### Post by Yezinki on 2008-11-28
Try K3b.

---

### Post by gpsmikey on 2008-11-28
One approach would be to download the trial version of Image 4 Linux from Terabyteinc ( [http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm) ) and create the bootable CD.  You can boot that then use it to write/validate directly to a writable CD or DVD.  That would allow you to try their software (which is really very good) but in addition, it would write then validate what was written to your CD allowing you to verify your drive was working ok (or not) and since the bootable version is stand-alone, it eliminates any possible problems with Ubuntu or the burning software you were using.

mikey

---

### Post by HDTimeshifter on 2008-11-28
Yeah, K3B was going to be my next approach.

It seemed to have problems just reading from CD, so I'll try that before wasting any writable CDs.

Edit:
I downloaded K3b and tried a clone copy which hung up and slowed way down just like Brasero and reported errors, so I aborted and tried a normal copy, which copied a 45 minute CD to image in under 2 minutes and burned a CD in under 2 minutes at 457k/s or so.  So I guess Brasero and K3b clone both hang up when there are scratches, resulting in a bad bit, while K3b's normal copy must use audio error correction to bypass those occasional bad bits.

---

