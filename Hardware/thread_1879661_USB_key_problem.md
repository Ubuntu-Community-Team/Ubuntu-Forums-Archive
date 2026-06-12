---
title: "USB key problem"
date: 2011-11-12
forum: Hardware
---

### Post by abrazafi on 2011-11-12
Hi,

My USB memory stick 16 Gb is unreadable...The brand is “Verbatim STORE N GO”
Tried to reformat it with linux basic tools without any success.

I'll need help on how to recover/format this memory stick.
Since I am a newbie, please explain me step by step.
Any suggestion will be welcomed.

Note that I am in remote city with limited Internet access and any
program downloading or any “apt-get install” is not possible.

Thanks for your support,
Abdon.

---------------- Herewith my tentatives using different basic tools:

1- Make startup disk / tried to ERASE DISK, ie, the content and got the 
following error message: “org.freedesktop.UDisks.Error.Failed:Error creating partition table: helper exited with exit code 1: error calling fsync(2) on /dev/sdb: Input/output error”

2- fdisk
  >sudo fdisk /dev/sdb
      Device contains neither a valid DOS partition table, nor Sun, SGI or OSF
      disklabel
      Building a new DOS disklabel with disk identifier 0x85e12edd.
      Changes will remain in memory only, until you decide to write them.                                  
      After that, of course, the previous content won't be recoverable.
                                                                                                                                              
      Warning: invalid flag 0x0000 of partition table 4 will be corrected 
      by w(rite)

      Command (m for help): w
      The partition table has been altered!

      Calling ioctl() to re-read partition table.

      Error closing file


3- cfdisk

 The tool lets me to format the memory stick without any error message.
 I got:


   >sudo cfdisk /dev/sdb

   Disk has been changed.

   WARNING: If you have created or modified any
   DOS 6.x partitions, please see the cfdisk manual
   page for additional information.

Then the memory stick is still unusable/unreadable!

4- sfdisk

     > sudo sfdisk /dev/sdb
     Checking that no-one is using this disk right now ...
     OK

     Disk /dev/sdb: 15296 cylinders, 64 heads, 32 sectors/track

     sfdisk: ERROR: sector 0 does not have an msdos signature
     /dev/sdb: unrecognized partition table type
     Old situation:
     No partitions found
     Input in the following format; absent fields get a default value.
     <start> <size> <type [E,S,L,X,hex]> <bootable [-,*]> <c,h,s> <c,h,s>
     Usually you only need to specify <start> and <size> (and perhaps <type>).


     /dev/sdb1 :0 16
     /dev/sdb1          0+     15      16-     16383+  83  Linux

     /dev/sdb2 :16 15280
     /dev/sdb2         16   15295   15280   15646720   83  Linux
     /dev/sdb3 :
     /dev/sdb3          0       -       0          0    0  Empty
     /dev/sdb4 :
     /dev/sdb4          0       -       0          0    0  Empty
     New situation:
     Units = cylinders of 1048576 bytes, blocks of 1024 bytes, counting from 0

    Device Boot Start     End   #cyls    #blocks   Id  System
    /dev/sdb1          0+     15      16-     16383+  83  Linux
    /dev/sdb2         16   15295   15280   15646720   83  Linux
    /dev/sdb3          0       -       0          0    0  Empty
    /dev/sdb4          0       -       0          0    0  Empty
    Warning: no primary partition is marked bootable (active)
    This does not matter for LILO, but the DOS MBR will not boot this disk.
    Do you want to write this to disk? [ynq] y
   /dev/sdb: Input/output error

   sfdisk: Failed writing the partition on /dev/sdb
   Re-reading the partition table ...
   /dev/sdb: Input/output error
   Error closing /dev/sdb

   If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
   to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
   (See fdisk(8).)

5- parted

   >sudo parted /dev/sdb
   GNU Parted 2.3
   Using /dev/sdb
   Welcome to GNU Parted! Type 'help' to view a list of commands.
   (parted)mklabel msdos                                                    
   Error: Input/output error during write on /dev/sdb                        
   Retry/Ignore/Cancel?

---

### Post by Paddy Landau on 2011-11-14
May I suggest you use either GParted or Disk Utility.

Try to delete the partition then recreate it and format it as FAT32.

If they are unable to do anything, either you have your read-only switch set (if the USB stick has such a switch) or the USB is damaged.

Bear in mind that this will destroy any data on the USB stick.

---

### Post by WasMeHere on 2011-11-14
Hi Abdon,

If you can download the tools suggested by Paddy Landau, use them! Otherwise it should be possible also with ***fdisk*** and ***cfdisk***. *Edit: Gparted is included in the Ubuntu live disks*

I recommend that you delete the partition(s), then make new partition(s). A FAT32 partition with boot flag and lba flag will be good if you also want to use it as a live USB drive.

Have fun finding out :-)
Olle

---

### Post by abrazafi on 2012-02-16
Hi,

Thanks... I did all your suggestions without any success.
The USB key still has problem.

Best regards,
Abdon.

---

### Post by Paddy Landau on 2012-02-17
> **abrazafi said:**
> The USB key still has problem.
In that case, your USB flash is probably damaged. Sorry.

---

