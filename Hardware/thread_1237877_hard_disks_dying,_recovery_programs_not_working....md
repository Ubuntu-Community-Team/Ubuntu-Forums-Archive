---
title: "hard disks dying, recovery programs not working..."
date: 2009-08-11
forum: Hardware
---

### Post by rhcm123 on 2009-08-11
I have 2 hard disks that are suffering much problems and giving me a headache. I've connected them to a working linux install but i can't get any kind of diagnosis on their problem. Perhaps you all could help me get a hold on these problems, as i'm a software guy, not a hardware guy.

Before you ask, the interface these disks are connected to is good, i used two different disks on it.



DISK ONE:
This is a seagate 80 GB disk. I have no bloody clue what's on it. My computer gave named it /dev/sde. 

running parted /dev/sde causes parted to immediatley crash. no errors at all. as in:
```

ussr@USSR-LAPTOP:~$ sudo parted /dev/sde
[sudo] password for ussr: 
ussr@USSR-LAPTOP:~$ 

```

running testdisk /dev/sde says: Unable to open file or device /dev/sde
running fdisk /dev/sde says: Unable to read /dev/sde

I don't have a clue what's wrong with this drive, but its not my main priority, and i'm prepared to cast it away if need be.



DISK TWO:
A 250GB maxtor drive, this origianlly was the main disk of a server. (it is very old and not RAID capable, therefore one disk). This disk was also assigned /dev/sde. This guy has a story behind him - i issued the command rm -r /share, which is the mount point for the second partition. (EDIT: I forgot to mention that i wanted to use rm -r /share/*, because share was still mounted). a few seconds later, i got the dreated 'DRDY err' (see [this]("http://ubuntuforums.org/showthread.php?t=937872") for an explanation). Soon after, the kernel paniced and the system shutdown. I rebooted and got GRUB error 17. Somthing bad happened there. :P

I tried parted /dev/sde, and it took almost 6 minutes to load parted up, and the print command caused it to hang. Same problem with testdisk - it took 5 minutes before it even began to output info. Ordering it to recover caused nothing (apparently) to happen.

However, running fdisk /dev/sde was not a total loss (I also noticed that it took forever to boot before parted was run, but instantly after parted was run).

Verifiying the partition table in fdisk says "11401 unallocated sectors".
Printing the partition table gives: (this appears correct)
```
Disk /dev/sde: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00090605

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        3039    24410736   83  Linux
/dev/sdf2            3040       30394   219729037+  83  Linux
/dev/sdf3           30395       30515      971932+   5  Extended
/dev/sdf5           30395       30515      971901   82  Linux swap / Solaris
```

Asking it to fix the partition order returns "Nothing to do."

Also, in the syslog, i noticed these errors in a repeating string:
```

Aug 11 18:51:11 USSR-LAPTOP kernel: [ 5911.936883] sd 13:0:0:0: [sde] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 11 18:51:11 USSR-LAPTOP kernel: [ 5911.936895] end_request: I/O error, dev sde, sector 64
Aug 11 18:51:11 USSR-LAPTOP kernel: [ 5911.936904] Buffer I/O error on device sde, logical block 8
```

Also, when i removed this disk, i noticed it was extremely hot, if thats relevant. (It could have presumably fried itself in the low-ventaliation server).

---

### Post by rhcm123 on 2009-08-13
24 hours bump. I also would request some extra focus on disk 2, as i need some config files off it that i forgot to backup.........

---

