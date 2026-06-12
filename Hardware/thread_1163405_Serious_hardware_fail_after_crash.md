---
title: "Serious hardware fail after crash"
date: 2009-05-18
forum: Hardware
---

### Post by whoop on 2009-05-18
I was running Ubuntu and running a Ubuntu livecd inside vmware server. I was downloading some data inside the guest os (memory usage was well beneath any threshold on the host and the guest) and all of a sudden the host and guest froze. I restarted X but it didn't come back up. I reset the machine and it got stuck halfway booting without giving any error messages. 
I booted from livecd and liveusb but it got stuck also. 
I powered down the machine, removed the power cable and gave it a 15 minute rest.

At this moment I thought my motherboard is borked as it cannot boot from hd, it can not boot from cd and it cannot boot from usb.

When I connected and started the machine backup, I got s.m.a.r.t. messages for the primary hard disk, but I was able to boot from livecd. I was not able to mount any of my 4 partitions with the livecd. I am running repair tools from a boot floppy as we speak but I don't feel positive about recovering my data a.t.m.

P.S. Asus p5b motherboard, I was running ubuntu 9.04 with ext4

The question is, what happened? Is this just a hard-disk gone to hell or is there something else that could be wrong? When I was running the machine at least 1 of the partitions was completely unmounted for the entire session. How can it be that I can't mount that partition either? Could it be that there is not something wrong with the disk-surface but with the heads? If that is the case why is recovery software able to read allot of data and have serious problems with small blocks of data on every partition?
Any information concerning this issue would be greatly appreciated.

---

### Post by Dark_Stang on 2009-05-18
Sounds like your hard drive crashed, probably due to a head strike. When your hard drive crashes like that it doesn't discriminate which partition gets hit. Most of the time the entire hard drive will become unreadable.

---

### Post by whoop on 2009-05-19
Well, I replaced the drive. Luckily I had about 98% on backup. Reinstalled my OS's and put necessary backups back onto the system.
I will be analysing the drive later on, to see if I can read data back (just for experimentation). If anybody has tips on data recovery I would like to hear about it. I have used testdisk and autopsy in the past.

---

