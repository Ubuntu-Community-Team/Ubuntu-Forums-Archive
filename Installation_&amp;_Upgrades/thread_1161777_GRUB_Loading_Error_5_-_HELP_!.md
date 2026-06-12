---
title: "GRUB Loading Error 5 - HELP !"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by lollo45 on 2009-05-17
This is my first experience ever with a Linux OS.

I have a Windows XP Professional OS on my desktop computer.
I want to have both Windows XP and Ubuntu installed, and being able to choose at bootup which one to use.

I downloaded Ubuntu 9.04 desktop i386. As recommended, I checked that the file was intact with MS5SUM. No problem. 
Then I burned on a CD. I installed Ubuntu from the CD.


Now:

In one of the question screenshots during installation, the one where I selected to let me choose at start which OS to use each time, I found it strange that it was saying "no operating system on this computer" when in fact, as I said, I have Windows XP installed.
Why wasn't it recognizing that there was Windows XP installed?
Anyway, I continued and completed the installation.

Now, when I try to bootup I get the error

GRUB loading Error 5

and it stops there!

I cannot start Ubuntu without the CD !!!!!
and
I cannot even start Windows (I don't know how to do it, since it does not get to the point where I can choose)

Please help me. I have been reading some threads, looks like it's a partition or drive problem.

I have two drives, C and D.
C is supposedly my main drive, where XP is. I don't know on which drive Ubuntu was installed.

I went to the Terminal, and I ran "sudo fdisk -lu", a command I found in a previous forum thread and I got this (I hope it helps to understand) :

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x679f50ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd2f195d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   387809099   193904518+   7  HPFS/NTFS
/dev/sdb2       393046290   398283479     2618595    5  Extended
/dev/sdb5       393046353   397930049     2441848+  83  Linux
/dev/sdb6       397930113   398283479      176683+  82  Linux swap / Solaris


(By the way... My data (my files) is safe, right ? I don't want to overwrite my files with some wrong partitioning...)

Please help !
Thank you very much.

---

### Post by quixote on 2009-05-17
The bad news is that you got dumped in at the deep end.  The good news is that fdisk is saying your partitions are still there and it's recognizing the Windows drive as bootable.  Grub error 5 means it's having trouble understanding the parition table.  That's serious, but not hopeless.  Main thing is NOT to do a lot with that computer until the partition table is resuscitated.  You could overwrite data you don't want to overwrite.

It looks like you have two physical drives. (That's what the "sda" "sdb" means.  Separate partitions (also called "drives" in Windows) on one physical drive would be sda1, sda2, and so on.)

```
sda has one partition, sda1, 80GB, bootable, all Windows
sdb has two partitions, total 200GB
   sdb1 bootable Windows
   sdb2 extended (a partition that can have logical partitions under it)
      sdb5  the linux partition
      sdb6  linux swap
```

So you have two Windows installs according to fdisk.  Is that right?

First step: fix partition table.  Second step: fix grub.

First step: I like testdisk, which is a text-based, kind of ugly, but effective recovery tool. There are others.  You can search for "partition recovery."   Testdisk looks scary, and asks strange-looking questions, but you can pretty much accept the defaults and it fixes things. (But do read everything carefully, take your time, and do the best you can to make sure the choices sound sensible!)

Boot from Ubuntu LiveCD.  Enable universe repository.  Install testdisk. (This will install only into temporary memory, since you can't write to the LiveCD.)

Add line to /etc/apt/sources.list ;
```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe
```

and then run the following commands to install testdisk.
```

ubuntu@ubuntu:~$ sudo apt-get update
ubuntu@ubuntu:~$ sudo apt-get install testdisk

```
Then run testdisk on your two physical drives, sda (as below) and sdb
```

ubuntu@ubuntu:~$ sudo testdisk /dev/sda

```

Assuming at this point grub gives you some other error on start up (21 I think??) which means it can't find the boot partition.

Second step: rebuilding grub.  The instructions here are the easiest I've found:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Come back and tell us how it goes!

---

### Post by lollo45 on 2009-05-24
Thank you for your message and for your help!
 
It took me a few days to try and do this, I had to buy an external hard drive and I had to back up all my data just in case something goes wrong.
 
I learned how to enable universe repositories, I installed Testdisk, but there are several commands to choose from and I don't know which ones I should use and how.
 
I ran Testdisk on both "sda" and "sdb".
 
After the command "Analyze" (both Quick and Deep) I try to use also "Change Geometry". But when I go to "Change Geometry", it asks me the new number of partitions to recreate from the current partitions. I execute it but I don't change the current number, because I don't know what number to put. So I don't know if that does anything to it.
For example, it says you can put a number from 1 to 63 (63 is the current number). 
So which new number should I pick? Random ? 55? 62? 1? Boh.
 
Anyway, after running Testdisk with these very few commands I could understand (Analyze and Geometry without touching numbers) the Error 5 is still there.
 
What can I do?
 
I would have never imagined that installing a Linux OS for the first time would have created such a major problem. Is Linux always so complex ?

---

### Post by lollo45 on 2009-05-28
Can anybody help ?

---

### Post by quixote on 2009-05-28
lollo45:  unfortunately it's pretty much a case of the blind leading the blind here.  I'm not an expert on testdisk or fixing partitions.  I've done it a few times, hoping for the best, and managed to fix things, but that's the extent of it, so just remember, this is not an expert speaking! :?

1) Do NOT mess about with geometry unless you are 100% certain you have the right numbers.  (E.g. the manufacturer's web site says those are the ones to use.)  That's low level formatting that could make your drive completely unusable if it's wrong.  Partition tables are on top of geometry so to speak.  If you had an apartment building, there's the floor plans, and the doorbells with names next to them.  Geometry is the floor plans.  Change that, and you're moving walls.  The partition table is more like making sure the right name is next to the right bell, so when the system rings one of them, it doesn't get a wrong number.  So it's very good you didn't touch geometry!

2) Analyze does just that.  It doesn't fix anything unless you get to the "write" choice a few menu levels down.  It should give you some idea of how bad the trouble is.  Analyze should tell you about lost partitions or whatever other cryptic info it has.  I'm not sure at this point which options I used, and I don't have a spare hard drive to try things out on. I've listed a couple of sites below that have better info than I can give you.

There are how-to sites for testdisk:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)  bit intimidating, but it has useful screenshots
[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk) this is less visual, but gives a clear how-to on going through testdisk menus to recover a partition.

Hope this helps!

---

### Post by lollo45 on 2009-05-29
Quixote,

I understand you points and I thank you very much
for giving me this information.

Lollo45

---

