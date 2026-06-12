---
title: "Hard Drive Recognition/Partitioning"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by drums907 on 2006-01-15
During the installation process the partitioning tool is run.  When it comes up it reports the wrong drive info.

IDE1 Master (hda) - 2.1 GB IBM-DTLA-307015
               pri/log    2.1 GB FREE SPACE

The drive model is correct but the drive size is incorrect.  The drive has a 15.3 GB capacity and I am using it strictly for Ubuntu installation.  The drive has 16383 Cylinders, 16 Heads, 63 Sectors.  I input the cylinders, heads and sectors in the boot paramaters.  boot: linux hd=16383,16,63 and it still shows the same partition table as before.  How do I get Ubuntu to recognize this drive for what it is?  I have tried installing this thing six or seven different ways and I still get the same drive parameters.

Thanks for any help you can give.

---

### Post by drums907 on 2006-01-18
EUREKA!!! I Found IT! There is a clipping jumper for older OSs that was installed on some IDE drives. Changed the jumper and set for 16 Heads and VOILA!!!! It is now recognized at full capacity!

---

