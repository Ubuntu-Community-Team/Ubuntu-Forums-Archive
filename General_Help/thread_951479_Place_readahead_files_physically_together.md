---
title: "Place readahead files physically together?"
date: 2008-10-18
forum: General Help
---

### Post by MacUntu on 2008-10-18
Readahead preloads all files needed during the boot process which is great but still those (for me 815) files are placed all over the disk.

We all know that sequential reads are way faster than random reads so I'm looking for a way to move those files physically together (eg. my defrag tool for Windows (Raxco PerfectDisk) allows to move those files to the beginnig of the partition).

Is there any way I can achieve that with Linux tools?

---

### Post by MacUntu on 2008-10-19
*bump*

For a better understanding: I'm trying to move the colored, maybe fragmented, files so that they are consecutively stored on disk for a better read throughput (which sucks according to bootchart):

[IMG]http://img.xrmb2.net/images/322734.png[/IMG]

---

