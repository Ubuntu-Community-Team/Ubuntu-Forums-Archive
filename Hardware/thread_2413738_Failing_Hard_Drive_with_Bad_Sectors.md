---
title: "Failing Hard Drive with Bad Sectors"
date: 2019-03-01
forum: Hardware
---

### Post by Redalien0304 on 2019-03-01
Have a Failing Hard Drive with Bad Sectors.
Have Backed HDD with Clonezilla.
When Try boot the Cloned Copy just hangs on the Ubuntu Screen with the moving Dots.
Have Tried Previous Kernel, Advanced Recovery options, just hangs.

Any would be appreciated Thanks

---

### Post by rbmorse on 2019-03-01
I apologize in advance if I'm stating what is obvious, but is the Clonezilla output you are attempting to use to boot the machine a compressed image file (Clonezilla's default) or a straight bit-by-bit copy of the original disk/partitions?  

The image file cannot be used directly to boot and run the machine it has to be restored to another media before it can be used.   

If the output is a straight bit copy (the dd option under the advanced menu) it ought to be usable, but you might have to disconnect the original storage device because it will have the same UUID as the cloned copy.

---

### Post by #&amp;thj^% on 2019-03-01
With Clonezilla and bad sectors, The read will fail rather than give you bad data. 
However, it depends on what level you're operating at as to whether you even try read it or not.

Of course, the drive cannot know whether your OS level filesystem is using a block or not.

It only knows whether it can read or write something and how many errors it had whilst trying.
For most of my quick and dirty methods I'll just use: "To move Linux installation 'cp -a' will do just great." Or ddrescue
Or if you want to continue with clonezilla see this for "expert mode":[https://sourceforge.net/p/clonezilla/discussion/Clonezilla_live/thread/fe3fef42/](https://sourceforge.net/p/clonezilla/discussion/Clonezilla_live/thread/fe3fef42/)
Good Luck.

---

### Post by Redalien0304 on 2019-03-01
No not Compressed Images. Disk to Disk option with in Advanced Mode with Rescue Option Selected.

---

### Post by tea for one on 2019-03-01
Did you have a separate swap partition before using Clonezilla?

Sometimes, a slow boot process indicates the OS is looking for a swap partition which hasn't been cloned.

As mentioned above, the UUIDs including swap are important.

---

### Post by Redalien0304 on 2019-03-01
no swap partition Installed DDresue-GUI 2.0.1

---

### Post by tea for one on 2019-03-01
How many partitions were on the failing disk?

---

### Post by Redalien0304 on 2019-03-01
Has 3 Partitions Ubuntu 18.04 sda1, Linux Mint 19 sda2, Backup for files sda3. linux mint sda2 does Boot but takes Longer to boot.

---

### Post by tea for one on 2019-03-01
As you can boot into Linux Mint, you should take this opportunity to copy all your personal files to an external device.

Then, you can either post your details via the boot repair procedure [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) or, if that doesn't help, then you can install fresh Ubuntu and Mint and pop in your backed up personal files.

My preference would be to start from scratch on your new HDD and reinstall your data.

Best wishes

---

