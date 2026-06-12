---
title: "Removing a PV from a VG that hasn't been used"
date: 2013-02-07
forum: Hardware
---

### Post by diehardyouth on 2013-02-07
Hi all,

So, I have the following setup:

- Ubuntu 12,04
- 1 6TB physical volume (the one with data) [ext4]
- 1 13TB PV (no data... I think?) [ext4]

Here is the story...

- I created an ext4 on the 13TB PV, added the 13TB to the VG to make a 13TB volume group.
- Everything went fine and then I ran:
```
resize2fs /dev/volgroup/volume
```
And to my surprise.. I couldn't resize past 16TB ! (crap! should have checked this first!).

So, nothing happened.. Now what I want to do is remove the 13TB PV from the VG and do something else with it... but I get the following error:

```
sudo vgreduce -t home_volume_group /dev/sdc1
  Test mode: Metadata will NOT be updated.
  Physical volume "/dev/sdc1" still in use
```

How can I safely remove this PV from the VG?


Thanks a bunch!

Harold

---

