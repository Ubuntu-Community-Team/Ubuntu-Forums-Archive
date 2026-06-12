---
title: "Guided partition not working when installing 8.1"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by tati on 2009-02-20
I'd like to install Ubuntu 8.1 on my Vista desktop. The installation DVD shows a guided partition of 8% Vista, 92% Vista but throws an error when I proceed with this partition. When I clear the error, the only option shown on the partition editor is to use 100% of the disk, thus wiping out my Vista partition. What is preventing me from using the guided partition?

---

### Post by Dies on 2009-02-20
A Vista partition should only be re-sized using the utility provided with Vista.

So boot into Vista, run disk management, choose to shrink your Vista partition as much as you want or as much as it will let you then try installing Ubuntu again.

---

### Post by tati on 2009-02-20
I had no problem using the guided partition on the 8.04 install DVD. Same computer, same Vista. Has something changed on the new install DVD?

---

### Post by konqueror7 on 2009-02-20
it is recommended that before installing on a partition that it should be defragmented/diskscanned first...

---

### Post by Therion on 2009-02-20
> **tati said:**
> I had no problem using the guided partition on the 8.04 install DVD. Same computer, same Vista. Has something changed on the new install DVD?
I believe something DID, in fact change.  I had zero luck getting my drive to properly partition using 8.10's installer.  Swap the CD to 8.04 and the install would go off without a hitch.  My solution was different, but my point is, in short, that I believe something did change between 8.04 and 8.10 as regards the installer/partitioner.

Possible solution:  Using a gParted LiveCD to pre-partition your drive (shrink your Vista partition, etc.) before rebooting to the Ubuntu LiveCD and trying to install again.  Frankly, I don't think that will work, but it's something to try.  Good luck!

---

### Post by tati on 2009-02-20
Thanks for the clarification, Therion. Is it a simple, discless upgrade from 8.04 to 8.10?

---

### Post by Therion on 2009-02-20
> **tati said:**
> Thanks for the clarification, Therion. Is it a simple, discless upgrade from 8.04 to 8.10?
You can use the Update Manager of your current intsll to upgrade, yes.  No discs required. 
I always *recommend* a clean install but, barring that, using the Update Manager to do a dist-upgrade is your next-best bet.

---

### Post by tati on 2009-02-22
I ended up using Gparted to shrink the Vista partition and installed 8.10 in the new partition. I went this route because 8.04 has display issues on my Dell Studio Hybrid and the screen sometimes goes black after installation.

I do think the partition editor has gone a step backwards in the 8.10 installer. The guided partition could lead a noob to accidentally wipe out their Vista partition and manual installation is not intuitive. I understand that Ubuntu is not yet entry-level but the partition editor was better in 8.04. At least my screen no longer goes black in 8.10!

---

### Post by sasully on 2009-02-22
There is a new graphical view of the existing and predicted partitions, in the Ubuntu 8.10  installer 'Guided partitions', but I can't find any way to alter them. IOW, I don't see any 'slider' in the 8.10 LiveCD installer , to let the user shrink or expand existing partitions.  There used to be one in the old installer. 

(There is still the 'Manual' option but that has never been noob-friendly, and still ain't.)

EDIT:  oops, I see on [this page]("http://www.psychocats.net/ubuntu/dualboot") that there is a slider on there...
guess I'll have to try again.

---

