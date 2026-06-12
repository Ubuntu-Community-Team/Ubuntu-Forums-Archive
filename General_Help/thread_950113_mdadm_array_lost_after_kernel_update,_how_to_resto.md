---
title: "mdadm array lost after kernel update, how to restore?"
date: 2008-10-16
forum: General Help
---

### Post by maxxum on 2008-10-16
I had an array /dev/md0 working fine until yesterday when (I guess) there was a big update (which by the way also broke my virtualbox, which had to be recompiled). So the /dev/md0 is gone. I have some ideas about reassembling it but I don't want to risk losing data. The devices in the raid1 array are sdb1 and sdd1.
```
 ls /dev/m
mcelog  mem     mixer   mixer1
```
```
sudo mdadm --query /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
```
```
 sudo mdadm --query /dev/sdb1
/dev/sdb1: is not an md array
/dev/sdb1: device 0 in 2 device undetected raid1 /dev/.static/dev/md0.  Use mdadm --examine for more detail.
sudo mdadm --query /dev/sdd1
/dev/sdd1: is not an md array
/dev/sdd1: device 1 in 2 device undetected raid1 /dev/.static/dev/md0.  Use mdadm --examine for more detail.

```
```
sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2bddc22b:e11d1959:8f234c9d:e4a85fce
  Creation Time : Tue Sep 30 11:31:50 2008
     Raid Level : raid1
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Oct 15 12:17:59 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f60262bc - correct
         Events : 0.22


      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       49        1      active sync   /dev/sdd1

```
```
sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 2bddc22b:e11d1959:8f234c9d:e4a85fce
  Creation Time : Tue Sep 30 11:31:50 2008
     Raid Level : raid1
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Oct 15 12:17:59 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f602629a - correct
         Events : 0.22


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       49        1      active sync   /dev/sdd1

```

What I seek is:
1) Uncouple the drives, back up all my data to a third drive.
2) Reassemble the raid array. 
What is a safe way to do this? the system is Hardy 64 bit.
PS: the /etc/mdadm.conf is gone and there is an empty directory /etc/mdadm .

---

### Post by fjgaude on 2008-10-17
Try force assemble:

```
sudo mdadm --assemble -f --scan
```

and see if that works.

The array is in tack so somehow you should be able to assemble it. If the above doesn't work try this: remove mdadm, delete /etc/mdadm/mdadm.conf, reboot. Then re-install mdadm... a new mdadm.conf file will be created. If you reboot the array should come up, or else do a simple assemble.

---

### Post by raykroeker on 2012-11-06
Is there a prescriptive process to be used when upgrading the kernel when you have an array?

I've experienced this myself but every time have relearned recovery.  What should I be doing instead?

Raymond

---

