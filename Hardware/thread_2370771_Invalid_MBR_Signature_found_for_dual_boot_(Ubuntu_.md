---
title: "Invalid MBR Signature found for dual boot (Ubuntu + Windows7)"
date: 2017-09-07
forum: Hardware
---

### Post by learnboot on 2017-09-07
My dual boot laptop (Ubuntu 16.04 and Windows 7) suddenly stopped  booting. The GRUB menu did not show up. I tried the utility boot-repair  and it did not even show "Recommended Repair" in the small popup window.  
  The BootInfo summary was uploaded at: [https://paste2.org/I7XU5F19](https://paste2.org/I7XU5F19)

  The hard drive I am trying to fix (or recover data from) is /dev/sda, a Samsung SSD 840.

Before the booting problem occurred, I did the following: I booted from grub into Windows 7, did some work there, put the computer in sleep mode (still in Windows 7), tried to wake up the laptop, saw a blue screen for a few seconds.


From the summary:
  [HR][/HR]  Drive: sda _____________________________________________________________________ Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes
  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
  Invalid MBR Signature found.
  ======================== Unknown MBRs/Boot Sectors/etc: ========================
  Unknown MBR on /dev/sda
  00000000  49 00 01 00 00 00 00 00  00 00 00 00 00 00 00 00  |I...............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
  **...**


Any idea what I should do to fix it or recover the data from it? Will ddrescue help?

---

### Post by oldfred on 2017-09-07
Was sda gpt or MBR? Or was it UEFI or BIOS boot?
Windows 7 is usually BIOS, but you show UEFI entries?  Windows 7 DVD has to be copied to flash drive and files moved around/renamed to make it UEFI bootable for UEFI install.

If it was gpt, MBR only has one entry saying drive is fully gpt to show old tools that are not gpt aware that drive is formatted.

What does gdisk show?
sudo gdisk -l /dev/sda

And then to run commands on drive with gdisk
       sudo gdisk /dev/sda
Command (? for help): ?

    
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 

If MBR, you can see if testdisk shows partitions.

---

