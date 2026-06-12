---
title: "Fresh install over gutsy help"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by i-like-knives on 2009-07-24
I have 8.04 LTS on disc. Need direction on how to do a fresh install and (delete?) Gutsy, as I am somewhat new and didn't realize gutsy was run out of support. I looked an searched but cannot find specifics.

---

### Post by merlinus on 2009-07-24
You can install the new version into the same partitions that gutsy currently resides on.  You may need to select manual at the partitioning screen, so write down the partitions beforehand, e.g. sda3 for /.

---

### Post by i-like-knives on 2009-07-24
Thanks, but I have no idea how to do a fresh install, could you help, please??
I do have 8.04 LTS on CD (how do I kn ow if its a "Live" cd ??

---

### Post by merlinus on 2009-07-24
Boot from the cd, and select install at the menu.  It will ask a few questions (e.g. language, keyboard layout, location) and then go to the partitioning screen.

But check the cd for errors at the same menu first.

And if you ae not sure about your partitions, post results of this command entered into a terminal:

```
sudo fdisk -l
```

---

### Post by i-like-knives on 2009-07-24
Merlin, when you say "boot from the CD, does that mean turn my machine off and start it with the CD in the drive?? If not how do I boot from the cd I made??
Sorry, never done this before.
(But check the cd for errors at the same menu first). What menu?? Again, I apologize, I know some, but I may need the kindergarden version here.
This is the partition result.
Thanks again for your help


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002bbf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38166   306568363+  83  Linux
/dev/sda2           38167       38913     6000277+   5  Extended
/dev/sda5           38167       38913     6000246   82  Linux swap / Solaris
glenn@Buntu:~$

---

### Post by merlinus on 2009-07-24
Restart with the cd in the drive, and hopefully it will boot from it.  If not, you will have to press a key to select booting from the cd before the hdd.  You will have to look in the computer docs, or perhaps google the brand and model.

If all is well, a menu will appear with a number of choices,  Check the cd for errors first, and if it is ok, then select install.

Since ubuntu is the only operating system on your hdd, select use entire disk at the partitioning menu.

---

