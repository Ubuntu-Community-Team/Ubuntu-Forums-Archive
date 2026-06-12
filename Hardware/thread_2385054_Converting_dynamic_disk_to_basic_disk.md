---
title: "Converting dynamic disk to basic disk"
date: 2018-02-15
forum: Hardware
---

### Post by opino72 on 2018-02-15
Hello!
I have a kinda important problem today., i&#8217;ll try to to explain it correctly, I really need help!

I have a Windows 7 / Ubuntu 16.04 dual boot.
Here is the hard drive setup :
1 SSD for Windows
1 SSD for Ubuntu
3 HDD for data and softs, including 2 basics and 1 dynamic.

I had a USB key that I thought could be infected so I booted from the BitDefender DVD to analyse it (it was ok). Then I restarted the computer, booted on Windows and it showed a message saying my partition named E: could have problems, then that it can&#8217;t be checked because of a software problem. When I typed my password I couldn&#8217;t login. I unplugged the HDD and and rebooted, I could log in fine. I booted onto Linux and I could access the files just fine.

The thing is : I am not loosing data here, but it&#8217;s annoying because it&#8217;s ALL my softwares and games (~1TB). Formating the HDD and reinstalling all of this would be a pain in this ass.

I read that I had to convert it from dynamic to basic.

What I tried unsuccessfully : 
On windows : 
dskprobe.exe
> not detecting any HDD

On Linux :
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
> It showed that I wasn&#8217;t in NTFS for that HDD
sudo fdisk /dev/sde
t
1
7
w
(and repeated for the three partitions then rebooted)
> can&#8217;t access the HDD anymore on Ubuntu (no changes on Win)
> no filesystem type 
> no mountpoint
> no label
> can&#8217;t change the partition type because there is none (&#8220;No partition is defined yet!&#8221;)

I really need to fix this fast, I need to work. Thank you.

---

### Post by oldrocker99 on 2018-02-15
Ah, Windows! This program should help you read ext* file systems, and, although it says it's for ext2 and ext3, it works with ext4 partitions. Here it is on SourceForge: [https://sourceforge.net/projects/ext2fsd/](https://sourceforge.net/projects/ext2fsd/).

---

### Post by oldfred on 2018-02-15
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.

You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 

   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) 
   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005) 
   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

