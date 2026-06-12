---
title: "Dualboot installation. Issue with partition"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by hhhmmm on 2009-07-09
Hello all.

I am very new to Ubuntu or Linux in general. I thought I'd give it a try but am having problems during the install. Any help is appreciated.

I'm trying to dualboot Ubuntu with XP.

I have run the Installer from the CD & restarted. I get to %5 when its working on the partition but it stopped. the window says "creating ext3 file system for / in partition #1 of loopback". It will just stay at 5%, I left it overnight (around 7hrs) & it was still at the same spot.


I then tried installing from the liveCD. I choose the "along side XP" option & slide the partition size to around 18GB (the auto installer was choosing around 17.5). It would start the "resizing partition" but would stay on 0% for about 10mins & then I get  "An error occurred while writing to storage device. The resize option has been aborted".
  I then have the option to Prepare Partition my self but I'm not sure what to do.


I downloaded the Wubi-Installer & tried but got error again for ext3 when its trying to partition.

I ran the CD check & it came back good.



Is there something I can do to solve this so the auto installer can work or do I have ot manually partition the drives when it gives me the option when trying from the LiveCD. If so, how do I do that.

I was hoping this would be simple. Thank again for any help.

---

### Post by merlinus on 2009-07-09
If you are wanting to shrink the xp partition whilst installing, make sure to delete temp and other unneeded files and defrag it several times first.  That may be the problem...

---

### Post by hhhmmm on 2009-07-09
I just did a format/install of XP about 2weeks ago & I defragged once.

---

### Post by merlinus on 2009-07-09
You might run checksums on your downloaded .iso files:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If they check out, make sure you burn them at no more than 4x speed.

---

### Post by hhhmmm on 2009-07-09
The did check out.

I ran the installer off the CD & I also tried after downloading the wubi-installer.

---

### Post by hhhmmm on 2009-07-10
any other suggestions?

---

