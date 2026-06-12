---
title: "Read EXT4 Partition on USB-Connected 3.5&quot; GPT HDD from Linux or Windows?"
date: 2024-09-22
forum: Hardware
---

### Post by ebsf on 2024-09-22
I have a modern 4TB 3.5" SATA 6.0 Gbps backup drive formatted via GPT, the main partition on which has an ext4 file system, which I have to read / copy for a recovery operation.



The hardware available is a USB drive enclosure and a ThinkPad that dual-boots Linux and Windows 10.



**[B]The problem**[/B] is that (a) while Windows has utterly no trouble doing this for USB- connected NTFS partitions, it does not read (or write, for that matter) EXT4-formatted partitions; and (b) Linux finds it impossible to read or write USB-connected 3.5" HDDs  (but somehow has no difficulty reading or writing 2.5" HDDs (*[I]cf*[/I]. SSDs) via a USB adapter, however).



Several third-party Windows drivers exist for reading ext4 partitions but these consistently trigger a BSOD when launched with the drive enclosure powered on (and vice versa).  Presumably, they would work without difficulty were the drive connected to an internal SATA adapter.



It isn't clear that WSL solutions work for a USB-connected drive but confirmation one way or the other would be helpful.



**[B]The question**[/B] is how to read a USB-connected EXT4 partition connected to a Linux / Windows dual-boot laptop?  *[I]I.e.*[/I], any Linux- or Windows-based solution would be welcome, and so this is expressly being judiciously cross-posted.

---

### Post by oldfred on 2024-09-22
If you want to share data with Windows use NTFS, but make sure Windows fast startup is off. Note that Windows updates may turn fast startup back on.

How are you mounting partition(s)?
If with fstab many settings required.
 			 				[INDENT] 					[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[/INDENT]



If just clicking with file browser, best to label partitions, so mounted by label not some long UUID.

Similar recent post:
[https://ubuntuforums.org/showthread.php?t=2501064](https://ubuntuforums.org/showthread.php?t=2501064)

from lsblk, my external SSD in a m2 to USB adapter:
```
[FONT=monospace][COLOR=#000000]Samsung SSD 850 EVO M.2 250GB  sdb                232.9G                                                     [/COLOR]
                               &#9500;&#9472;sdb1      vfat     510M                   EFI System Partition             A02D-F0F6 
                               &#9500;&#9472;sdb2      vfat     5.9G        m2_fat     m2_fat                           4738-7B8C 
                               &#9500;&#9472;sdb3      ext4    35.2G        m2-noble   m2_noble                         09a68bbd-3d26-4630-b18e-7c687761aa36 
                               &#9492;&#9472;sdb5      ext4   127.4G        m2_data    m2_data                          0c374965-53c6-437c-a2ad-f0508486f9d5
[/FONT]
```

---

### Post by yancek on 2024-09-23
'm not aware of any windows system being able to read/write to an ext4 filesystem by default, only third party software is used.  WSL is basically a type of virtual software and I can't imagine there is any way using it would give you more options than a default install to hardware.  You might want to wait for other opinions since I've never used WSL just read others experiences with it. 

What is the problems with the 3.5HDD?  What specifically happens when you try to read/write to them?

---

