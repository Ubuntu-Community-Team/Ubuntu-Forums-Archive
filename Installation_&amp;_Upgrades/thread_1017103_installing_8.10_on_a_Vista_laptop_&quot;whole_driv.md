---
title: "installing 8.10 on a Vista laptop &quot;whole drive&quot;!"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by aqk on 2008-12-20
Hi-  I have previously installed Ubuntu 8.04 on laptops with Vista, no problem.
Dual booting with Grub works great.
 I now have a Vista system which I have partitioned with about 15 free gig.
When I start the Ubuntu 8.10 install it seems to want to use the WHOLE DRIVE, whether I choose manual or automatic. So I obviously exit the install.
 It shows a cute picture of the whole drive, and says "using 100%"
No indication that Vista or other partitions are already there!
I do not recall 8.04 install doing this threatening step.

  Is this just bad wording or install design?  Will it let me choose my own Ubuntu 8.10 partition and swap partn afterwards in step 5 (or 6?), and leave my already existing partitions intact?

---

### Post by SunnyRabbiera on 2008-12-20
you may have to manually edit your partitions or something though I am surprised it wants to take the whole drive.

---

### Post by damnhappy on 2008-12-20
I have the same exact problem- no partitons show up when trying to install 8.10.  I have a Dell M1210. Been searching the forim but haven't found anything that works.

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

So when you choose the manual partitioning option, there is *no* indication that your windows partitions exist? Am I getting that right?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNhZ0ACgkQyLm4ydrABvckMgCfWJPod2w8/EJGXq+2kyhqjqOV
hcsAn2GIjIhF1eY0LXLOtx3+Cig5/mLr
=JXC/
-----END PGP SIGNATURE-----

---

### Post by aqk on 2008-12-20
> **Carl Hamlin said:**
> 
 there is *no* indication that your windows partitions exist? Am I getting that right?

 you are getting that right.

But Windows Vista boots OK on C:  and I even have a 10Gig D:drive for data...

I reserved 15 gig or so of blank space in the middle for Ubuntu.
Interesting, tho-  The unformatted space and the 10Gig NTFS D: partition are NOT part of an extended partition- they are completely independent partitions.
Maybe if I somehow incorporated them into an extended partition?

I would try doing this with an old copy of PartitionMagic-8 I have, but it gives me an error- tells me that my hard-drive is totally fscked!  Even though My C: and D: partitions are fine. 
Very puzzling.  
  Without INSTALLING Ubuntu 8.10, could I use it to repartition the HD?

---

### Post by aqk on 2008-12-22
ADDENDUM-
 PartitionMagic-8 shows ONE BIG partition for the whole disk, and that there is an error on it.

  I  DLed the latest GPARTED-CD and booted from this. It also showed one big partition for the whole disk.

  Yet Vista boots and runs OK and shows my three NTFS partitions correctly-
 i.e.  C:  D:  and E: 
But they are shown as 3 independent partitions, 
not C: and then ( D: + E: ) in an extended partition. 
And I know there is some unused space on the disk for installing U-8.10

Any utilities around (either Linux or Windows) that I could use to reconcile some of this stuff? WITHOUT destroying my MBR? 
  -Thanx

---

### Post by aqk on 2008-12-22
Consider this problem closed.

I DLed the gnu "TESTDISK" for Windows and ran it.
It quickly found all my Windows partitions, corrected some bad size errors, and I then rewrote the Partition info with it.
 The hard disk now looks OK to other systems, and I am now busy installing Ubuntu 8.10 on the drive's free space.

  I recommend "Testdisk" to anyone who has a partition screw-up problem of this sort.
  AND when I get some $$ in bank acct after xmas, I'll donate some money to the testdisk author! :)

---

### Post by Carl Hamlin on 2008-12-22
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

That's excellent news. Thanks for letting us know, and sorry I wasn't of more immediate help.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEUEAREDAAYFAklP1rkACgkQyLm4ydrABvd8UQCWL9DGieS9ITM+yUwx3Fcun8Ip
jQCgz5vANDZrVOLuSBwU7HEpX8eujFA=
=0nt6
-----END PGP SIGNATURE-----

---

