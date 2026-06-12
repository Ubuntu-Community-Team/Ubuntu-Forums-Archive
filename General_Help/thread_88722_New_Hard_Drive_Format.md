---
title: "New Hard Drive Format"
date: 2005-11-10
forum: General Help
---

### Post by johnfarrow on 2005-11-10
If one buys a new 300 GB hard drive and installs Ubuntu,  will it format to the full capacity?:-({|=

---

### Post by RAOF on 2005-11-10
Yes.  Why wouldn't it?

Actually, I suppose that some filesystems wouldn't like a 300GB partition (does FAT go that high?).  But any of the filesystems Ubuntu supports (ext3, reiserfs, XFS, anything but FAT) should do fine.

---

### Post by matthew on 2005-11-10
Yes.

Bear in mind, though, that it may say something less than 300 Gb after it is formatted. Part of that is because manufacturers have changed how they report storage size. This wiki page will help you understand what I mean.

[http://en.wikipedia.org/wiki/Gigabytes]("http://en.wikipedia.org/wiki/Gigabytes")

By the way, I have noticed that Ubuntu reports the size of my hard drives, usb disk and external hard drive in gibibytes. I appreciate the accuracy. (Read the article to know what I am talking about)

---

