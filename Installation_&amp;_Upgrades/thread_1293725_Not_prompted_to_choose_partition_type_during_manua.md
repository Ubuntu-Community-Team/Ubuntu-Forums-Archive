---
title: "Not prompted to choose partition type during manual partition server install"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by mo-regard on 2009-10-17
I am trying install ubuntu server on a dell 2950 with a hardware Raid5 totaling 6TB of data.
I was in the process of doing a manual partition of the disk, how ever I am not being prompted to select the partition type.

1. I can choose the hard disk which is identified as SDA with 6.0TB
2. I then select YES to create a new empty partition table
3. I then select the free space available
4. I then select create new parition
5. I then select the size as 4GB   ( i want this to be the  / partition with a boot flag on)

It is as this point I should be prompted for the Partition Type(primary or logical) BUT I AM NOT PROMPTED, it skips over this and goes to Partition Location (beginning or ending)

I have installed this numerous times, but it is the first time that I have ever seen this issue. 

If I continue along with the installation, I then get an error when GRUB begins to install as it tries to install it to "hd0"

What can I do?

---

### Post by mo-regard on 2009-10-19
RESOLVED!!
I figured it out. The issue is related to the size of the array.
I changed my configuration to include 2 arrays.
The first physical disks i setup as Raid1 with 2 x 1.5tb drives.
The second array I setup as Raid5 with 3x1.5tb drives.
Once I did this, I was able to complete the install and specify the Partition type as primary.
Grub then installed without an issue

---

