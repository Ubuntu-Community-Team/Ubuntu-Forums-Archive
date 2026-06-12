---
title: "USB Drive gets corrupt after copying from Linux"
date: 2010-11-10
forum: Hardware
---

### Post by vikrang on 2010-11-10
To be honest , i do not mean that Linux is corrupting the USB drive. Windows does not recognize the disk after a write operation performed in Linux even though the target USB is FAT / FAT 32 partitioned.
 
I try to copy a file in the disk...When I reboot into Windows , immediately it pops up a window that "the disk may not be properly formatted Do you want to format?" I choose Yes and it gets detected and is usable ..The moment I reboot back to Linux and write a file for use in windows , I get the same error message (even though the partitioning had been done using WIN)
 
Is it a problem with the stick?

---

### Post by thomaswei on 2010-11-10
Did you click the eject/unmount button before removing the stick?

---

### Post by vikrang on 2010-11-10
I remove the stick after the shutdown operation in Linux (Sometime just before the monitor blacks out)..So it is unmounted while I remove it

---

### Post by thomaswei on 2010-11-10
Did you try unmounting the stick manually after formatting it in windows and later writing to it in linux to make sure it was umounted properly?

Maybe over the CLI by typing 

```
umount -v /media/<USBStick>
```so you should see possible errors

---

### Post by bavamurali on 2010-11-10
I got the same problem but the thing even after formating usb is not shown in windows

---

### Post by vikrang on 2010-11-10
I do not think "umount" could be the issue ..The reason being I format this time in Linus as a FAT 32 partition and copy , umount and reboot to WIN - still same dialog box asking to format,,,
 
I also used HP - USB formatter and performedd a proper format (not Quick) ...Still it is not working...
 
Is there any utility to check USB for errors? or do I use testdisk, scandisk etc?

---

### Post by ajgreeny on 2010-11-10
> **vikrang said:**
> I do not think "umount" could be the issue ..The reason being I format this time in Linus as a FAT 32 partition and copy , umount and reboot to WIN - still same dialog box asking to format,,,
 
I also used HP - USB formatter and performedd a proper format (not Quick) ...Still it is not working...
 
Is there any utility to check USB for errors? or do I use testdisk, scandisk etc?
There is **dosfsck** from the command line, (see *man dosfsck* for manual) but I have absolutely no idea how good it is at checking disks for the sort of problem you are seeing; I think it is more for file-system problems in an OS, not just for files on a memory stick.

Have you looked at the disk with the System ->Administration ->Disk Utility?  It may tell you something useful.

It may be worth trying to format as ext2, just to see if it will work in that; I realise it will be no good for use on a windows box, but it may give some clues about whether it is a hardware problem.

---

### Post by aytech on 2010-11-10
> **vikrang said:**
> To be honest , i do not mean that Linux is corrupting the USB drive. Windows does not recognize the disk after a write operation performed in Linux even though the target USB is FAT / FAT 32 partitioned.
 
I try to copy a file in the disk...When I reboot into Windows , immediately it pops up a window that "the disk may not be properly formatted Do you want to format?" I choose Yes and it gets detected and is usable ..The moment I reboot back to Linux and write a file for use in windows , I get the same error message (even though the partitioning had been done using WIN)
 
Is it a problem with the stick?

Did you try to eject the stick after partitioning and insert it again? if the error will appear. maybe even to reboot into Win again and try. 
I had similar problem, and think its the the problem with the stick

---

### Post by vikrang on 2010-11-16
Thanks ..I found out that there is no problem with the stick...Just installed Mint 10 by making LIve USB from LiLi creator for Windows...
 
I am going wrong somewhere in linux 
 
1. Should I use mkdosfs -F 32 /dev/sdx (or)
2. mkdos.vfat /dev/sdx  (Think this uses FAT16)
3. Any other additional switch in "dd"
 
Just for my understanding
 
Work around is available and u can of course use some GUI...

---

