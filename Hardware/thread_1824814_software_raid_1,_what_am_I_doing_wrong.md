---
title: "software raid 1, what am I doing wrong?"
date: 2011-08-14
forum: Hardware
---

### Post by pencils on 2011-08-14
Hi all,

Long story cut short: did a fresh install of 11.04 and now struggling to get my existing RAID 1 array to work.

OS is installed on /dev/sda1

Two more HDDs: /dev/sdb and /dev/sdc were previously (yesterday) working fine in RAID 1.

I tried to get the RAID array working and screwed something up, so I took drastic measures and "started again". This involved:

breaking down the existing array, zero-ing super block. I could then successfully mount /dev/sdc1 and see all my data.

Then I re-created the RAID array with just /dev/sdc1 and a missing device, this seemed to work ok

Then I re-added /dev/sdb1 back to the array, it took some time but cat /proc/mdstat said it was all ok

Now I have two problems: I do not have a mdadm.conf file, and cannot seem to do mdadm --detail --scan >> /etc/mdadm/mdadm.conf, I get access denied

And I cannot mount my new array (sudo mount /dev/md1 /mnt/mydir) gives me "wrong fs type".

What am I doing wrong? Do I need to re-create the FS on the /dev/md1, but how do I do this without hosing all the data?

HELP!

---

