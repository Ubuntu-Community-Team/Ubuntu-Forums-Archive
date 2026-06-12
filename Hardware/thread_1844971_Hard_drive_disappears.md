---
title: "Hard drive disappears"
date: 2011-09-16
forum: Hardware
---

### Post by mysticBoer on 2011-09-16
I hope somebody can help me at least find the problem.

Here's my system spec:
```

CPU : Core i7 860 (LGA 1156)
MB : DH55TC (Tom Cove - Intel)
Memory : 8Gb Kingston ValueRAM
Hard drives: 2 x SATA ST31000525SV 1TB Seagate

```

My system is setup as follows:
```

OS : Ubuntu Server LTS
Extra 'roles': LAMP,Samba,OpenSSH 
Partitions:
   /dev/sda
       /dev/sda1 - Ext4 Partition - Mounted on '/' - 8GB
       /dev/sda2 - Software RAID Partition - Rest of disk
   /dev/sdb
       /dev/sdb1 - SWAP - 8GB
       /dev/sdb2 - Software RAID Partition - Rest of disk
   /dev/md0 - Ext 4 Partitioon - Mounted on '/data' - 1.8TB

Software RAID : RAID0

```

Use of system:
This is meant to run as a 'headless' appliance which does tcpdump capturing and analysis to the '/data' partition. I use RAID0 because I need maximum speed without any redundancy requirements.

My problem:
I built the machine, installed it as an ether tap where it was needed and logged in the next day to check on some statistics. When I logged in, I was unable to see /dev/sdb at all and my /dev/md0 partition was mounted as read only. 

I proceeded to restart the box only to be greeted by a message stating that '/dev/md0' could not be mounted and that I could  press 's' to skip mounting.So, I press 's', go into the box and do a 'cat /proc/diskstats' only to see that /dev/sda is the only drive in the machine. 

I restart the machine again (by turning it off and back on) and then it works again. I can restart it and go mad after this and nothing will break. But after another day, same story.

The S.M.A.R.T status' of the drives report 'Disk Healthy'. The disks pass the SeaTools for Windows (I tested them in another machine) without issues. 

Are there any other tests you can recommend, for instance, to test the IDE/SATA controller perhaps or some other recommendations.

---

