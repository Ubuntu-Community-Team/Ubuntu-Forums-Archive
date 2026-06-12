---
title: "CD Burner Malformed URL"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by saking on 2007-03-29
I am using Kubuntu Dapper Drake.

I reciently replaced my CD-ROM drive with a CD-RW/DVD-ROM drive.

I can read music CDs, data CDs and data DVDs without problem.

When I put a blank CD-RW into the drive I get a "Blank CD-RW" icon on my desktop.  However, when I double click to open this with Konqueror, I get a "Malformed URL" error message.

I found a similar post from more than a year ago that does not seem to have been fully resolved; but, the first suggestion in the thread was to type the following in a terminal:

```
sudo hdparm /dev/hdc
```

When I do this I get the following:

```
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

---

### Post by saking on 2007-04-04
OK, so no one seems to know the answer to this.

Let's try another approach.

When I remove a piece of hardware, and replace it with another piece of hardware, is there something I should do to let Ubuntu know that I have installed new hardware?

---

