---
title: "Renaming partitions on Desktop"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by Robert_P on 2009-06-19
Using 9.04, I have installed a second hard drive (160GB) and partitioned into three partitions. These have been set up to automatically mount on boot up.
However, the partitions appear on the desktop as 55.2GB media, 31.5GB media and 73.4GB media, giving no indication of the contents.
Is there some way of renaming the partitions as they presently appear on the desktop?

---

### Post by Revolutionary101 on 2009-06-19
I don't think it is possible to rename these partitions.

---

### Post by louieb on 2009-06-19
Give the partition a label. thats the name that will show up on the desktop.

to give a partition a label:
Install Gparted. (9.04 only) After its installed open system>admin>partition editor. 

One of the recently added features of Gparted is to add/change a partitions label. 


May have to logout or restart for the new name to take effect.

IF they are ext3 partitions you can use e2label - see **man e2label**

---

### Post by Robert_P on 2009-06-19
Thanks a million louieb. My copy of Gparted has the "Label" greyed out. Obviously I don't have the latest edition of Gparted. However that can be rectified and you have put me on the right track

---

### Post by -kg- on 2009-06-20
Something you might try is to launch Nautilus, right-click on the drives in question, and select "rename."  I don't know if that will work.

---

### Post by coffeecat on 2009-06-20
> **Robert_P said:**
> My copy of Gparted has the "Label" greyed out. Obviously I don't have the latest edition of Gparted.

If you've installed Gparted from the repositories in 9.04 (Jaunty) you have a version that will handle labelling. The problem is that you're trying to label a partition that's mounted. Unmount the partition (you can do that from the 'Partition' menu in Gparted) and then the 'label' option will become available.

If you need to label your root partition, you will not, of course, be able to do this while running from the hard disc. Simply use Gparted in the live CD for this. And you could use Gparted in the live CD to label the partitions in the second drive if you want.

---

