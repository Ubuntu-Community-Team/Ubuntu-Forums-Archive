---
title: "UNR Install Grabs only Small Part of Vacant Partition"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by Peter108 on 2009-10-03
Howdy.

I tried to install UNR 9.04 onto my Samsung N110 netbook using a bootable flash drive I created.  What's cool about the N110 is that it ships with a 160GB HDD already partioned: 6GB for recovery, ~75GB for XP, and ~75GB  just waiting to have UNR installed on it.  

The install went smoothly, with the partitions showing up in the installer as described above.  So I chose automatic partitioning and finished my install.  Only when a subsequent download blew up for lack of disk space did I notice that the installer had created a tiny 2.4 GB partition and installed UNR onto that, not the full 75GB partition.

So now if I rerun the installer and reach the part where it "prepares disk space"  I see:
Windows Vista (loader) /dev/sda1 6GB
Windows XP /dev/sda2 70.0GB
(/dev/sda3)[my desired target partition] 70.5GB
Ubuntu 9.04 /dev/sda5 2.3GB
swap /dev/sda6 172.5 MB

If I continue, I'm told that Ubuntu will install on /dev/sda7 and 8, so I abort.  If I simply boot up the installed version of UNR, both the XP partition and /dev/sda3 are recognized and readable.

Can anyone tell what might be happening here and how to fix it?  I'm not a total noob, but I'm not keen on the idea of manual partitioning, either.  Thoughts?

Many thanks.

---

### Post by mikewhatever on 2009-10-03
Apparently. it looks like the system partition got the space allocated for swap (2.3GB) and vise versa. Boot from the USB you created and delete these partitions with System->Admin->Partition Manager. If it's not there, install it with **sudo apt-get install gparted**.

---

### Post by Peter108 on 2009-10-04
Thank you!

For whatever reason, GParted wouldn't let me delete the offending partitions (well, specifically it said they were mounted, but I couldn't umount them from a terminal).

So I went over to the Dark Side (i.e., XP) and blew out the partitions from *its* partition tool. Then I went back into Ubuntu, expanded the 75GB parition to "the right" to consume all remaining space, re-partitioned, re-installed, and now all's well.

---

