---
title: "problems with a windows partition, is it the HDD?"
date: 2012-10-26
forum: Hardware
---

### Post by nekroskoma on 2012-10-26
about a day go my win7 partition decided to not boot and proclaim that some system files were currupted and it could not repair it either

i decided to do a complete reformat since 12.10 came out but while i was trying to save things from the win partition i kept getting a I/O error and nothing was copied

after i reinstalled win 7 it spit out 0xc00000e9, the new ubuntu partition had no problems so i just just wnt ahead and made the entire disk ubuntu but then it started giving me I/O errors and saying packages were not installed

my machine is working fine in a dual boot right now my gut is telling that there is something up with my HDD like bad sectors or the like

the only thing that has changed in the past month was a got a new graphics cardbut it was fine with that beside one bluescreen, the card is pci3 but its running as a pci2 also during that time i upgraded my bios i tried to install without the card but still go the same errors

---

### Post by ahallubuntu on 2012-10-26
Check the hard drive's S.M.A.R.T. health.  In Ubuntu you can use/install GSmartControl (the command line version is "smartctl").  You could also use the same thing with the Parted Magic Linux distro that has it built in ("Disk Health").

---

### Post by nekroskoma on 2012-10-26
passed, i ran chkdsk /f on the windows partition and it did find some bad sectors

but now when i boot its spitting out the same error code and this time sayin that the kernal is either missing or corrupted

im not sure how to proceed

---

### Post by nekroskoma on 2012-10-26
its ******, now Ubuntu went into kernel panic when rebooted and now it wont even start

the livecd still sees the drive but trying to boot from the dive just does not work now

id say its new hdd time

---

### Post by ahallubuntu on 2012-10-26
So what else does S.M.A.R.T. control say besides "Passed?"  What about the Attributes tab?  Any lines highlighted in red?  Is the raw value for Pending Sector Count higher than 0?

If you have at least 1 Pending Sector, you are going to have trouble.  Sometimes zeroing out the whole drive can clear those sectors, but if not the drive is probably bad.

---

### Post by nekroskoma on 2012-10-26
is their some way to do that over the live cd or similar

---

### Post by ahallubuntu on 2012-10-27
Yes, using the Parted Magic Linux distro.  Google for it.

---

