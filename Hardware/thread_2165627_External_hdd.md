---
title: "External hdd"
date: 2013-08-05
forum: Hardware
---

### Post by UncleMonty on 2013-08-05
I am using ubuntu 12.04 LTS. 

My external HDD is now read only. How can I make it read/write? Is there anything I can do to diagnose the problem? 

What information do people need regarding the hardware?

---

### Post by Bashing-om on 2013-08-05
UncleMonty;
The quick response;
Is the external hard drive formatted for windows ? And did you (UN)safely remove the drive at some point ... such that the device was marked as "dirty" upon reuse ? If marked as "dirty" the system protects your data by mounting it as read only, until the file system is manually corrected.

If Windows... try plugging it back into a Windows' environment and then "safely" remove it there.

[INDENT][INDENT]just a thought 'till we know better
[/INDENT][/INDENT]

---

### Post by peter16 on 2013-08-05
I suppose there are two alternatives:
[LIST=1]
[*]You do not have the rights to make changes to the folder that the partition is mounted to. 
[*]The harddrive/partition is damaged; and you may need to run a diagnostics. 
[/LIST]

I think you can run a diagnostics with the program Disk Utility. Be sure to back-up!

---

### Post by UncleMonty on 2013-08-05
1. I ran check file system ran via disk utility - system clean
2. The Format is  fat32
3. The drive it seems was unplugged without being properly ejected

Is there anything I can run to make it read/write? (It's the back up drive of my computer and it contains ALOT of data so would like to avoid reformatting if I can). 

Is there a command or anything I can run in terminal please?

---

### Post by UncleMonty on 2013-08-05
delete

---

### Post by oldfred on 2013-08-05
Linux only does minor repairs to Windows file systems. You have to run chkdsk from a Windows repairCD or flash drive. 

Also NTFS is much better file system over FAT32 as it has a journal and can store files over 4GB.

---

### Post by UncleMonty on 2013-08-05
I haven't got any windows machines - only mac and linux.

---

