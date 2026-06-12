---
title: "Data Recovery on NTFS Partition Using Ubuntu 12 (x86)"
date: 2013-02-12
forum: Hardware
---

### Post by jyorkcar on 2013-02-12
Hi,
 
I'm trying to recover an accidently "formatted partition," using the  Ubuntu operating system.  I have already created an image of the  partition using "ddrescue" commands and now I need to be able to mount  the image to view the files.  How do I perform this next step?  I am  getting various errors when I run "ntfsck -n imagefile"  For example, I  get several errors like so, "ntfs_mst_post_read_fixup_warn: magic."
 
 **Background info**:
 
The drive is 250GB, which is composed of several partitions; a 100GB  partition of which has my customized Windows 7 installation that I am  trying to recover.  I was actually in the process of upgrading my  computer from HDD to SSD and somewhere along the way the drive in  question gave me errors about needing to run chkdsk from Windows, but  that failed with some error about not being able to write the log file.   I somehow stumbled upon a recovery partition, began to run it thinking  it would fix my problem, but apparently this is where the accidental  formatting occurred.  I have run a program called EaseUS on the drive,  which shows some of my files are still present on the partition, but I  am unable to recover anything without paying some fee (which I cannot  afford).
 
 **Additional**:
 
I am new to Ubuntu and still learning how to use the various commands.  So please bare with me.
 [B]
Some Technical Details[/B]:
 
eee@eee-1015PN:/media/eee/WD-Green1/linuxrecov$ **sudo ntfsfix -n imagefile**
Mounting volume... ntfs_mst_post_read_fixup_warn: magic: 0xa67da1e6   size: 1024   usa_ofs: 13558  usa_count: 12683: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x57452840  size: 1024   usa_ofs: 16329  usa_count: 13544: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xbe6dd42c  size: 1024   usa_ofs: 8252  usa_count: 2010: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x92d5f951  size: 1024   usa_ofs: 30892  usa_count: 37627: Invalid argument
$MFTMirr does not match $MFT (record 0).
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... ntfs_mst_post_read_fixup_warn: magic: 0xa67da1e6   size: 1024   usa_ofs: 13558  usa_count: 12683: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x57452840  size: 1024   usa_ofs: 16329  usa_count: 13544: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0xbe6dd42c  size: 1024   usa_ofs: 8252  usa_count: 2010: Invalid argument
ntfs_mst_post_read_fixup_warn: magic: 0x92d5f951  size: 1024   usa_ofs: 30892  usa_count: 37627: Invalid argument
OK
Comparing $MFTMirr to $MFT... FAILED
Correcting differences in $MFTMirr record 0...OK
FAILED
$MFTMirr error: Invalid mft record for $MFTMirr.
Corrupted file $UpCase
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
No change made
eee@eee-1015PN:/media/eee/WD-Green1/linuxrecov$** sudo fdisk -l imagefile**
 
Disk imagefile: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders, total 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e697373
 
This doesn't look like a partition table
Probably you selected the wrong device.
 
    Device Boot      Start         End      Blocks   Id  System
imagefile1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
imagefile2   ?  1917848077  2462285169   272218546+  73  Unknown
imagefile3   ?  1818575915  2362751050   272087568   2b  Unknown
imagefile4   ?  2844524554  2844579527       27487   61  SpeedStor
 
Partition table entries are not in disk order

---

### Post by Mark Phelps on 2013-02-13
Some folks will recommend using Testdisk -- and while that has worked well for them, I have never had it work well for me.

In my long experience, Windows utilities are BEST at manipulating Windows filesystem partitions; Linux utilities, at manipulating Linux filesystem partitions.

You should download and burn the Minitool Partition Wizard Boot CD (from a Windows PC). That is a free Windows partitioning utility that understands NTFS partitions. I don't know if the FREE version has the option to recover partitions -- but you can try it and see.

If it doesn't, you could consider purchasing the retail version and using it.

Once-click partition restoration would be a LOT less work than using RecoverMyFiles to get your files back -- which will take HOURS.

---

### Post by oldfred on 2013-02-13
Microsoft calls its repair console recovery and the vendor calls the restore to factory new recovery, so confusion among recovery tools is not unexpected.

I would try testdisk. But the vendor recovery restores system to as purchased and erases old partition table and writes the Windows partition, usually erasing all your old data, although their may be options to just refresh Windows.

Your partition table looks like it is gone and many Windows tools need to see NTFS partitions in partition table and in partition's PBR or boot sector.

Testdisk may be able to restore old partitions and possibily find PBR backup. But if restore started to overwrite data then Mark Phelps suggestions of trying to find the data may be best choice.

       repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by jyorkcar on 2013-02-13
I have tried using TestDisk without success.  It does find a bunch of  partitions, how I don't know nor do I understand how there's tons of  them.  When trying the option of going through the lists it creates and  pressing the "P" key to show the files, I cannot locate my files  anywhere in question.  As I said in the original post, another program  has somehow located some of my files, but the problem is I don't know  how.  I have no idea of the location of the files - by sectors or  partitions.  I'm at a loss and TestDisk so far is very difficult to use.

---

### Post by oldfred on 2013-02-13
Testdisk does find all the old partitions. So if you changed them even just a little it may find all those alternatives. You have to have some idea of what your partitions were and select that combination, where nothing overlaps with previous or deleted partitions. The more you have changed partition the more difficult it is to figure out.

---

### Post by jyorkcar on 2013-02-15
I'm ready to give up on partition recovery and instead focus on just file recovery.  I can run programs in Windows that can locate some of my missing files, but cannot recover the partition.  Using TestDisk, I cannot locate and restore the partition in question.  I know it was originally a 100GB, and actually the first partition on the disk, but TestDisk finds so many partitions of various sizes and none of them lists the files I need.  I have also attempted recovering the rebuild bootsector/repair MFT (whatever those two options are).  Also, when I try looking at the MFT option in TestDisk it says, "MFT and MFT mirror are bad.  Failed to repair them."  It seems the partition information, however formed, is corrupted to the point of no repair.  However, it is very odd that some of the other programs I have used can locate files called $MFT, $BOOT and so forth.  It would seem that there is a way to extract these files to bring the partition back to life?  Is there a way to manually recover the partition?  I just don't know enough about NTFS filesystems, but it seems the ingredients are still present to whip-up a new functional partition with the data in place.

---

### Post by Mark Phelps on 2013-02-15
Did you try using the MiniTool Partition Wizard? Did it provide you the option to Recover the NTFS partition?

---

### Post by jyorkcar on 2013-02-15
It doesn't show the files I need, but it does list a 100GB partition.  Is there a way for me aside from using TestDisk to work on an image file instead of the actual drive (all the programs I'm finding seem to only want to scan actual drives)?  I'm trying to prevent screwing it up any further before I'm certain whatever I do next will solve my problem.
 
Also, I have done some more reading about NTFS filesystems and my understanding is improving.  It seems the goal should be to recover a good MFT and that will solve my problem?  I mean, the various programs I have run can see a 100GB partition, it's just that the files are missing.  I'm just thinking if I can somehow re-create the MFT that it will give me access to the files?  I looked in TestDisk at another partition and it lists, "mft_lcn 786432," which I'm guessing is the sector location of the MFT.  I also noticed that from the 100GB partition it lists exactly the same thing.  It seems maybe I can scan the drive, examine missing files along the way, and rebuild the MFT?  I haven't come across a program that can do this when both MFT and the mirror are corrupt - they just offer me the chance to backup files in a 1-by-1 fashion.

---

