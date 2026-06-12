---
title: "How to move RAID drives from NAS to computer"
date: 2014-07-01
forum: Hardware
---

### Post by Silkefot on 2014-07-01
The LAN port on my QNAP TS-201 NAS got fried but the disks are still ok.I wish I could put another NIC into the fried NAS but the port is soldered directly on the QNAPs mainboard. How do I assemble an array for the two RAID 0 disks in Ubuntu 12.04 LTS without loosing data? I have the following outputs:
```
****@ubuntu:~$ sudo mdadm --examine --scan /dev/sda1 /dev/sda2 /dev/sda3 /dev/sda4 /dev/sdb1 /dev/sdb2 /dev/sdb3 /dev/sdb4

****@ubuntu:~$ sudo sfdisk -l /dev/sda
Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     65      66-    530113+  83  Linux
/dev/sda2         66     131      66     530145   82  Linux swap / Solaris
/dev/sda3        132   60790   60659  487243417+  83  Linux
/dev/sda4      60791   60799       9      72292+  83  Linux

****@ubuntu:~$ sudo sfdisk -l /dev/sdb
Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+     65      66-    530113+  83  Linux
/dev/sdb2         66     131      66     530145   82  Linux swap / Solaris
/dev/sdb3        132   60790   60659  487243417+  83  Linux
/dev/sdb4      60791   60799       9      72292+  83  Linux

****@ubuntu:~$ sudo blkid
/dev/loop0: UUID="4854a120-ce63-43e6-a043-ff2f947f9c5f" TYPE="ext4" 
/dev/sda1: UUID="3c2a691d-b918-59ed-8f17-3406692073e6" TYPE="linux_raid_member" 
/dev/sda2: UUID="9b0cfb3c-1175-538a-0278-87ad7b90d3fd" TYPE="linux_raid_member" 
/dev/sda3: UUID="627d8106-8d82-d5d5-2b13-8b4b562abb00" TYPE="linux_raid_member" 
/dev/sda4: UUID="f70f29d9-e904-8df1-f168-2a01f63a9588" TYPE="linux_raid_member" 
/dev/sdb1: UUID="3c2a691d-b918-59ed-8f17-3406692073e6" TYPE="linux_raid_member" 
/dev/sdb2: UUID="9b0cfb3c-1175-538a-0278-87ad7b90d3fd" TYPE="linux_raid_member" 
/dev/sdb3: UUID="627d8106-8d82-d5d5-2b13-8b4b562abb00" TYPE="linux_raid_member" 
/dev/sdb4: UUID="f70f29d9-e904-8df1-f168-2a01f63a9588" TYPE="linux_raid_member" 
/dev/sdc1: UUID="F2BE9BF2BE9BAD9B" TYPE="ntfs"
```

As you can see, the --examine --scan doesn't give anything back, but --examine tells me that the sda* and sdb* does not have any md superblocks. On sda and sdb the following is returned:

```
****@ubuntu:~$ sudo mdadm --examine /dev/sdb
/dev/sdb:
   MBR Magic : aa55
Partition[0] :      1060227 sectors at           63 (type 83)
Partition[1] :      1060290 sectors at      1060290 (type 82)
Partition[2] :    974486835 sectors at      2120580 (type 83)
Partition[3] :       144585 sectors at    976607415 (type 83)
****@ubuntu:~$ sudo mdadm --examine /dev/sda
/dev/sda:
   MBR Magic : aa55
Partition[0] :      1060227 sectors at           63 (type 83)
Partition[1] :      1060290 sectors at      1060290 (type 82)
Partition[2] :    974486835 sectors at      2120580 (type 83)
Partition[3] :       144585 sectors at    976607415 (type 83)
```

I did recover the mdadm.conf file with R-Linux and it had this inside:

```
DEVICE /dev/sd*[1-4] /dev/sd*[1-4]  

ARRAY /dev/md0 devices=/dev/sda3,/dev/sdb3 
ARRAY /dev/md5 devices=/dev/sda2,/dev/sdb2
```

I also tried the Linuxforums without luck...

---

### Post by tgalati4 on 2014-07-01
I bet you can find 4 contacts on the QNAP board that are pinouts to a USB  port.  Then you could solder a USB cable (or 1/2 of one) and use a USB-to-ethernet dongle.

You are assuming that the QNAP uses a mdadm-style RAID.  It probably uses a proprietary, or tweaked RAID that can't be read or assembled by mdadm.  That would explain the lack of google search results.  So now you are left with how to revive the network connectivity on the QNAP board.  If there is a USB port or pin-out, you might be able to plug it into a linux computer and just treat it as a super-large USB drive.

Try an explicit mount of a single drive:  [http://www.hexnut.net/2013/11/broken-raid-1-qnap-ts-201-how-i-got-data.html](http://www.hexnut.net/2013/11/broken-raid-1-qnap-ts-201-how-i-got-data.html)

Do you really have your QNAP set up as a RAID0?  Striping data across both disks without parity can make data recovery difficult.

---

### Post by Silkefot on 2014-07-02
It's two USB ports on it, one for making backups and one for printers. QNAP say's I can't use them to retrieve data so I haven't tried yet. Guess I should

---

### Post by tgalati4 on 2014-07-02
Don't use the external ports.  I'm talking about internal ports on the motherboard.  The external ports are designed to talk to peripherals, not other computers without an On-the-Go mode (OTG) versus the Host mode that it is currently configured.  You could probably find someone who has written a module to switch the external ports to OTG mode, but it not part of the original firmware--that would make too much sense.

Try pulling one of the drives out and mounting as suggested in the link that I gave.  If this drive is really RAID0 then you may be ship-out-of-luck (SOL).

---

