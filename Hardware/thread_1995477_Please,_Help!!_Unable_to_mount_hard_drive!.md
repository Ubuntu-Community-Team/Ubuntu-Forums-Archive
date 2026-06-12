---
title: "Please, Help!! Unable to mount hard drive!"
date: 2012-06-03
forum: Hardware
---

### Post by Dasha2012 on 2012-06-03
[LEFT]Good evening to everybody!
I have a problem with my hard drive and will appreciate any help!

I can't mount my hard drive neither under Ubuntu nor Windows XP. 

Ubuntu says:
----------
Error mounting: mount exited with exit code 18: ntfs_attr_open failed: No such file or directory
Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory
-------------


fdisk -l /dev/sdb  : (in Terminal)

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55911d8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


Thank you for help! =)

[/LEFT]

---

### Post by SirBlain on 2012-06-03
Is this an external drive or internal? What is it formatted as?

---

### Post by papibe on 2012-06-03
Hi Dasha2012.

Have you tried mouning it using the file manager (called nautilus).

If not, try this:[LIST]
[*]Open 'Home Folder'.
[*]Hold the key Alt to see the global menu, then go to 'Go -> Computer'.
[*]There you should see a list of devices including your NTFS partition. It should be named 'OS', or '250Gb Hard disk'.
[*]Double click on it, and it will be accesible immidiately right there (It will be usually mounted on the background to /media/some_disk_name).
[/LIST]
I hope that helps, and tell us how it goes.
Regards.

---

### Post by oldfred on 2012-06-03
If Ubuntu does not mount it, it may need chkdsk. Ubuntu will not mount NTFS that needs chkdsk to prevent further damage that a chkdsk might not then repair.

Have you run chkdsk on your NTFS partition. Ubuntu runs fsck on every 40 to 60 reboots to verify partition is ok. If external drive it may be d: drive or something other than c: drive in Windows.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Dasha2012 on 2012-06-04
Thank you for help )

This is an internal hard drive in my desktop computer. There is no OS installed on it, just files. It is formetted as NTFS.

Yes, I have tried mouning it using the file manager. The result is attached.

I will run chkdsk now and write the result in a few minutes.

By the way, I don't know whether this can help, but I've been experiencing problems with that drive for several months. Windows made disk check every second startup and the drive has already been unmountable for a few times, but everything was ok after restart. Unfortunately, it doesn't help me now.

---

### Post by Dasha2012 on 2012-06-04
CHKDSK in Windows XP failed:

--
chkdsk d: /r
The type of the file system is NTFS.
Volume label is DiskD.
Corrupt master file table.  CHKDSK aborted.
---

I have no idea how to fix that. I really need some files on the disk..
Please, help.. =)

---

### Post by wilee-nilee on 2012-06-04
> **Dasha2012 said:**
> CHKDSK in Windows XP failed:

--
chkdsk d: /r
The type of the file system is NTFS.
Volume label is DiskD.
Corrupt master file table.  CHKDSK aborted.
---

I have no idea how to fix that. I really need some files on the disk..
Please, help.. =)

Did you try this chkdsk command oldfred gave you.
> **oldfred said:**
> chkdsk drive /p /r

---

### Post by Dasha2012 on 2012-06-04
Yes, I tried:
--------
chkdsk d: /p /r
Invalid parameter - /p
--------

That's why I did it without "/p".

---

### Post by oldfred on 2012-06-04
The /p /r are options, you only use one at a time.

Usually chkdsk repairs things.  If you were having issues for a while it was telling you something. 

Under Disk Utility click on sdb and does it show Smart Data and is Smart Status green? I only know green is good but it has a lot of detail on drive and errors. A few errors can be ok, but increasing numbers over time show a problem.

If drive is ok, you can try this.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

