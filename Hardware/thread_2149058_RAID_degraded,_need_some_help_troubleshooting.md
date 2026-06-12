---
title: "RAID degraded, need some help troubleshooting"
date: 2013-05-27
forum: Hardware
---

### Post by X1R1 on 2013-05-27
Hello forum,

I have a samba server running Ubuntu Server 10.04.4 LTS and today I started getting lots of the following errors on console:

end_request I/O error, dev sda, sector [SOMENUMBER]

Upon rebooting (by keeping power button pressed (not even ctrl+alt+del worked), ubuntu does a disk check and then the server boots, no errors.

I went ahead and check my RAID health with:
#sudo mdadm --detail /dev/md0

And here is what I get:

/dev/md0:
        Version : 00.90
  Creation Time : Tue May 18 16:45:06 2010
     Raid Level : raid1
     Array Size : 976760768 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May 27 10:48:35 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : a7c3b861:f3cfb50b:0e619c2a:6e9739d4
         Events : 0.679696

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed

So, my questions:

1) Why does the second device appears as removed, but is not counted as failed (look above where is says "Failed Devices: 0")
2) How can I check the hard drive for errors if its now removed from the array?
3) Should I just get a new hard drive and replace this one?

Thanks for the help!

---

### Post by SaturnusDJ on 2013-05-28
1. I don't know for sure. Sometimes mdadm does things that are good but a little hard to understand.

2. Use the smartctl command.
To start, look at the current SMART data with:
```
smartctl -a /dev/sdb
```

To test:
```
smartctl -t short /dev/sdb
```
If the above does not give any hint of a failing disk at all, go for a long test.

3. Depends on the SMART results. But do expect to, yes.


Be sure to have a backup! Especially now you're running degraded.

---

### Post by X1R1 on 2013-05-28
Ok I am back with more information! as it turns out, the disk is totally dead (it isn't even detected by the BIOS anymore), so I was reading the steps required to replace the failed disk. Some documentation mentions marking the drive as failed and then remove it from the array (or else mdadm won't let you remove it). However, in my case the drive is already removed so I don't need to mark it as failed, right?

new disk is on the way so I would like to get a better understanding before adding the new drive.

@SaturnusDJ: thanks for the help! actually I wasn't able to use the commands since the drive won't even show on BIOS, but I appreaciate your help!

cheers!

---

### Post by SaturnusDJ on 2013-05-29
Well that's the answer to question 1. :)

You might need this one:
```

mdadm /dev/md0 --remove detached

```

---

