---
title: "Western Digital My Book Essential 1TB problem"
date: 2009-12-29
forum: Hardware
---

### Post by JustAnotherVagueAnon on 2009-12-29
Hello, I recently purchased a 1 TB Western Digital My Book Essential and I have the following problems:

When I first plugged in the drive (initially formatted NTFS) three different things mounted in /media. One was the drive, and two were images for software packages that are usually autorun by Windows. I reformatted the drive to ext3 hoping it would overwrite the images which were being automounted but they still pop up when I boot the drive. I was wondering if anyone else had used a Western Digital external HD recently and overcome this problem. I would like to make it so these two images are not automounted and I would also like to know where they're being found. As far as I know, everything was reformatted and if this is also somewhere on the drive I'd like to erase it so I can just use the drive with no bells and whistles.

Second, when I df -h, I see 17GB of 1TB are already being used although nothing's on the drive. Does formatting info really consume so much space?

---

### Post by JustAnotherVagueAnon on 2009-12-29
Found the answer. It's here if anyone else has this problem in the future.
[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

---

