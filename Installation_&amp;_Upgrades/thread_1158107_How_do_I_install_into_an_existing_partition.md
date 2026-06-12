---
title: "How do I install into an existing partition?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by Colin@oxford on 2009-05-13
I wish to install 9.04 alongside 8.10.  When I get to the partitioning page of the installation process, I cannot find a way of specifying that I wish the install to take place in a partition that I have already set up.  It lists all the partitions that I have, including recognising that one has 8.10 in it, but does not tell me where it will install it.  When I press "continue" it appears to resize one of my existing partitions, presumably to install there.  No amount of clicking on the partitions or the key to them seems to do anything.   How do I tell it to install where I want it?

---

### Post by oldos2er on 2009-05-13
Use manual installation, select the partition you want to install on, and mark it as / (root).

---

### Post by Colin@oxford on 2009-05-14
Could you explain how I get to "manual installation"?  I started from CD and clicked on the "install" icon on the desktop.  What should I have done instead?

---

### Post by Elfy on 2009-05-14
Carry on throught the installation - when you get to the partition setup part - choose manual.

You will then have your partitions available.

---

### Post by Colin@oxford on 2009-05-14
On the partition screen, I have two bars of colour showing the existing partitions in pretty colours, with a key saying what they called, and under the first what they contain (e.g. it says that /dev/sda1 contains Ubuntu 8.10).

I have three buttons:

Install side-by-side
Use whole disk
Manual partitioning

If I select the third, then the whole of the second bar turns orange, which to me indicates that it is going to repartition the disk.  I do not want that, I simply want to use one of the partitions that already exist.

---

### Post by oldos2er on 2009-05-14
Manual allows you to select any existing partition to install to, in addition to allowing you to create new partitions if you choose.

 More info at [https://help.ubuntu.com/9.04/installation-guide/i386/module-details.html#di-partition](https://help.ubuntu.com/9.04/installation-guide/i386/module-details.html#di-partition)

---

### Post by cbenitez on 2009-05-14
> **oldos2er said:**
> Use manual installation, select the partition you want to install on, and mark it as / (root).

After doing this, I understand that Ubuntu will install on the desired partition. My question is how will it partition the drive? Do you know what the default partition sizes are? I know that it will partition to swap, ext3, etc.

---

### Post by Colin@oxford on 2009-05-15
Ah, right.  The change to (apparently) reformatting the whole disk is rather frightening.  Now successfully installed - thanks.

And to answer cbenitez, the manual partitioning does not format anything by default, except, strangely, an existing swap partition, which it says it reformats.

---

