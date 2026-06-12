---
title: "external HDD failure after fsck"
date: 2013-09-16
forum: Hardware
---

### Post by maiandros on 2013-09-16
Hello mates.
Recently i`ve faced some problems with my external HDD (1.5Tb Western Digital)...it kept denying to copy or to delete files and folders. So i thought that it could be good to try to see if there are any errors in it and i booted with my Windows and ran a Chkdsk. I`ve tried to run 3-4 times the Chkdsk command but it was always closing by telling me that "unspecified error occurred 6672732e637878 560" and it it didn`t fix anything.
So i thought i could use the fsck command in my Ubuntu...i think that it`s here where i`ve messed up,cause i thought that my HDD was not mounted but i was wrong. 
Now I`m stuck with an external drive that it cannot be found neither in Windows nor in Ubuntu and i don`t know what to do to fix it.
I don`t know if it can give you some hint on what had happened but i can give you the results of the
 ```
fdisk -l

maiandros@maiandros-Aspire-5630:~$ sudo fdisk -l
[sudo] password for maiandros: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   132038234    66019086    7  HPFS/NTFS/exFAT
/dev/sda2       132038235   161335109    14648437+  83  Linux
/dev/sda3       161335294   234440703    36552705    5  Extended
/dev/sda5       161335296   173053951     5859328   82  Linux swap / Solaris
/dev/sda6       173056000   234440703    30692352   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930272256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
/dev/sdb2   ?  1953251627  3771827541   909287957+  43  Unknown
/dev/sdb3   ?   225735265   225735274           5   72  Unknown
/dev/sdb4      2642411520  2642463409       25945    0  Empty

Partition table entries are not in disk order

``` 

What do you think can we save it? I really need the things that i have in my HDD ...
Thank in advance to all of you=D>

---

### Post by oldfred on 2013-09-16
It looks like random data was written into partition table. Have you tried testdisk? It may find old partitions and let you undelete. If you changed partitions it may find multiple copies and you have to select the correct or version that does not have overlapping partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

    
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by maiandros on 2013-09-16
> **oldfred said:**
> It looks like random data was written into partition table. Have you tried testdisk? It may find old partitions and let you undelete. If you changed partitions it may find multiple copies and you have to select the correct or version that does not have overlapping partitions.

No...i haven`t tried TestDisk but this HDD had never had any partions, i really cannot figure out why it appears like 4 partitions now...it should have only one!
I`ll see what can i do with TestDisk and i`ll be back asap...

---

### Post by maiandros on 2013-09-16
Basically in the TestDisk when i choose the HDD for a partition table type selection it automatically redirects me to the [none] Non Partitioned Media instead of the [Intel] type..:confused: 
I`m in deep analysis now and waiting...

```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * DiskSecure MB          409 142 41 119790  20 38 1917848077

Bad relative sector.
 2 * Sys=43               121584  74  6 234785 103 28 1818575915

Bad relative sector.
 3 * Sys=72               14051  94 29 14051  94 38         10

Bad relative sector.
Only one partition must be bootable
Space conflict between the following two partitions
 1 * DiskSecure MB          409 142 41 119790  20 38 1917848077
 3 * Sys=72               14051  94 29 14051  94 38         10 
```

---

### Post by oldfred on 2013-09-16
It looks like it is trying to use the garbage data in your existing partition table as the starting point.

---

### Post by maiandros on 2013-09-17
Here is the Deep Analysis result: 

```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182402 255 63

The harddisk (1500 GB / 1397 GiB) seems too small! (< 3829 GB / 3566 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
>  FAT32 LBA            278231  69  6 465560 233 35 3009450747


[ Continue ]
1540 GB / 1435 GiB
``` 


When i press continue it gets me to this screen: 

```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182402 255 63
     Partition               Start        End    Size in sectors
>*** HPFS - NTFS              0  32 33 182401   3  2 2930270208 [OEDIPUS]**



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 1500 GB / 1397 GiB
``` 


If i press Enter it brings me to the screen: 

```
Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182402 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33 182401   3  2 2930270208 [OEDIPUS]


>[  Quit  ]  [ Write  ]
                              Return to main menu
``` 



Selecting this partition with the key P (list files) it shows me a list with my folders in it.
What should i do next?

---

### Post by oldfred on 2013-09-17
If it was NTFS you want to write that choice.
The * would make it primary bootable.

---

### Post by maiandros on 2013-09-17
Ok...i am about to sign this thread as SOLVED thanks to Oldfred...appreciate it mate! 
Just a couple of questions for you...is there a safe way to chkdsk and repair my disk in my Ubuntu and not in Windows?
Does the problem that started everything means that my HDD is abou to R.I.P and so I should buy a new HDD and copy all the content of this drive?
Even after all this when i`m trying to copy some files Ubuntu gives me the error "Error splicing file: Input/output error"...what do i have to do?

---

### Post by oldfred on 2013-09-17
Chkdsk is something you can only run from Windows. Best to have a Windows repairCD or flash drive and periodically run it. Ubuntu runs fsck automatically on its systems every 40 or 60 reboots. 

Can just be caused by abnormal shutdown or other minor issues. I would check Smart data from Disks or Disk Utility to see if that shows anything. All I know is passed is good. But it can run a lot of test and output lots of data.

If you have data that is only on this drive then I might add a drive. I backup most important data to a couple of DVDs every quarter and have most data on a couple of hard drives.

---

### Post by maiandros on 2013-09-21
Thank you again Oldfred.
I was trying to run some tests through Disk Utility but it keeps failing to finish them so i don`t have any other details other than it has 1319 Bad Sectors and an Error ID 197 with a warning in Current Pending Sector Count.
I just hope it will copy my data to the new disk and it will not crush during the process.
Take care and thank you for helping me!

---

### Post by oldfred on 2013-09-21
You are welcome. Hope you get all your data back.

---

