---
title: "easily expandable storage"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by Promythyus on 2009-10-24
Hi all,

I'll be short sweet and to the point. I've got a file server running ubuntu with a 1tb drive. My end goal is to be able to add space to /home/ by just sticking another drive in and running perhaps a few terminal commands, and I want /home/ to be seperate to the operating system, so that I don't have to cart all my data off the drive to reinstall the OS.

My thoughts:
install OS on a spare 80gb drive.
set up the 1tb drive as a RAID0 array, in the ubuntu installer set the partition directory to /home/

Then when I get another drive (soon) i can just add it to the RAID0 array, without having to format or such, correct?

Thanks.

---

### Post by mr_steve on 2009-10-24
Check into LVM. It's kind of tricky to learn, but once you have it set up, you can add a physical disk to your system and extend partitions onto it pretty easily. You'll have to re-format to set it up, unfortunately, and I'm not really sure of the best way to use it with a RAID configuration, but I use it for the drives in my file server and it works great.

---

### Post by powertower on 2009-10-24
Yes, LVM is magical

---

