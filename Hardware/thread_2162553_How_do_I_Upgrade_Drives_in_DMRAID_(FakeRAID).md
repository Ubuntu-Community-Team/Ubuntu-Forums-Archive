---
title: "How do I Upgrade Drives in DMRAID (FakeRAID)?"
date: 2013-07-15
forum: Hardware
---

### Post by LoungeLizard on 2013-07-15
I have a 11.10 system upgraded to latest everything and have a /Data partition configured on 4 - 320Gb drives configured using DMRAID as a RAID5 array.  I recently acquired a bunch of 1.5Tb drives and thought I'd upgrade my array with 4 new drives.  After a lot of fruitless searching (google is not my friend on this venture), I'm not finding the answers I need.  I don't feel comfortable to just go experimenting - I'd rather find the right answer before playing around too much.

My system has a BIOS setting for NVIDIA RAID disabled and the current array I have was built using FakeRAID.  The first attempt I made was simply removing one of the drives and replacing it with one of the new ones.  That only caused a large number of errors and I could not get the array to recognize the new added drive.  Replacing the new drive with the old gets me back and relieved some stress.  After I wiped the sweat off, I spent a few more hours doing more research and came up empty.  Since the drives were not configured using the Mobo BIOS tools, I am at a loss as to how I would "fail" a drive so the array knows I want to replace it.  Then, I assume after I replace the drive, the array will rebuild and I'll be back to where we were to begin with.  Repeating the process for all 4 drives in the array, I assume should work.  Once the 4th drive was replaced and the array brought back to normal, then I assume I should be able to expand the partition size of the array.  But, how this can be done without destroying the existing data on the current array is unclear to me.

Could someone help me in this process of replacing all my RAID drives and utilizing their maximum potential after replacement?

-- Da Lizard

---

### Post by Cheesemill on 2013-07-15
First things first is this FakeRAID or not?

You say you have RAID disabled in your BIOS which would mean that this isn't FakeRAID (dmraid) it is in fact software RAID (mdadm).

Can you please post the output of...
```
cat /proc/mdstat
```

---

### Post by LoungeLizard on 2013-07-16
This is definitely a DMRAID implementation.

```
~$ cat /proc/mdstat
Personalities :
unused devices: <none>

~$ sudo dmsetup info
Name:               nvidia_aafjfffa1
State:              ACTIVE
Read Ahead:         256
Tables present:     LIVE
Open count:         1
Event number:       0
Major, minor:       253, 1
Number of targets:  1
UUID:   DMRAID-nvidia_aafjfffa1

Name:               nvidia_aafjfffa
State:              ACTIVE
Read Ahead:         3072
Tables present:     LIVE
Open count:         1
Event number:       167007
Major, minor:       253, 0
Number of targets:  1
UUID:   DMRAID-nvidia_aafjfffa

~$ sudo dmraid -r

|----------+--------+------------------+----------+---------+----------------+---------| 
| Device   | Format | Name             |   Type   | Status? | Size (sectors) | ?       |
|----------+--------+------------------+----------+---------+----------------+---------| 
| /dev/sde | nvidia | nvidia_aafjfffa  | raid5_ls | ok      |      625142446 | data@ 0 | 
| /dev/sdd | nvidia | nvidia_aafjfffa  | raid5_ls | ok      |      625142446 | data@ 0 | 
| /dev/sdc | nvidia | nvidia_aafjfffa  | raid5_ls | ok      |      625142446 | data@ 0 | 
| /dev/sdb | nvidia | nvidia_aafjfffa  | raid5_ls | ok      |      625142446 | data@ 0 | 
|----------+--------+------------------+----------+---------+----------------+---------|
```

And I most definitely have RAID disabled in BIOS.  I set this up using DMRAID a couple of years ago. I recall using DMRAID since MDADM (at that time) had an issue with the NVIDIA chipset I have on this Mobo.  There is a lot of data on this array and I don't want to crap it out.  Since I don't have control from BIOS to set a drive to a fail state or mark it as bad or something, I am wanting to determine how to utilize DMRAID or something to mark a drive for replacement.

-- Da Lizard

---

### Post by LoungeLizard on 2013-07-18
Ping...  Anyone with a little insight?  Please...

-- Da Lizard

---

