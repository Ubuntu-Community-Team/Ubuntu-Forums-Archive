---
title: "[SOLVED] GParted: problem with FAT32 partition"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by fizikz on 2007-08-17
I have a 500GB (actually 465GB) external USB hard drive on which I am trying to rearrange some partitions. I currently have an extended partition with a 160GB partition and a 305GB partition inside. I am trying to resize the 305GB partition.

The problem is that there is an exclamation point icon in GParted right beside the 305GB partition. The error is: 'Unable to read the contents of this filesystem! Because of this, some operations may be unavailable.' Indeed, it doesn't allow me to resize the partition. However, the 160GB partition shows no such problem.

---

### Post by merlinus on 2007-08-17
Are you using gparted live cd?

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by fizikz on 2007-08-17
I'm using the GParted program installed in Ubuntu from the repositories.

---

### Post by merlinus on 2007-08-17
Use the live cd.  It is a newer version with more features and capabilities.

-merlin

---

### Post by fizikz on 2007-08-17
Thanks, the liveCD worked. I had to start it with the VESA drivers option (otherwise the screen was all garbled), and even then everything was black except for the GParted window; still, that's all I needed, and it solved my problem.

 As a further note, I see that version 0.3.4-8 is able to move partitions to the left. That's great, because the version (v 0.1) built into Ubuntu 6.06 is not capable of this. I was hoping to eventually be able to get around that problem, and now I can. Thanks again!

---

### Post by merlinus on 2007-08-17
Glad to hear it.

Also, the new version will allow you to shrink/grow partitions from either side, unlike the one on the ubuntu install cd.

-merlin

---

