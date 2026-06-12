---
title: "HDD Mounting Issue"
date: 2012-12-30
forum: Hardware
---

### Post by Ørion on 2012-12-30
Hey everyone.  I recently put Ubuntu 12.10 back on my desktop and am having issues mounting one of my hard drives.  Here is my layout:

/dev/sda - 60GB SSD - The drive with Windows
/dev/sdd - 500GB HDD - NTFS
/dev/sdb - 1TB HDD - NTFS
/dev/sdc - 1TB HDD - 100GB Partition for Ubuntu and 900GB NTFS Partition

Everything seemed to be working fine, and I can access all my drives, except for /dev/sdb.  If I attempt to access the drive in Dolphin (I'm using KDE) I get the error:
```

 p, li { white-space: pre-wrap; }  An error occurred while accessing 'Storage II', the system responded: The requested operation has failed.: Error mounting: mount exited with exit code 12: Failed to read last sector (1953515519): Invalid argument
 HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
    or it was not setup correctly (e.g. by not using mdadm --build ...),
    or a wrong device is tried to be mounted,
    or the partition table is corrupt (partition is smaller than NTFS),
    or the NTFS boot sector is corrupt (NTFS size is not valid).
 Failed to mount '/dev/sdb2': Invalid argument
 The device '/dev/sdb2' doesn't seem to have a valid NTFS.
 Maybe the wrong device is used? Or the whole disk instead of a
 partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```When I saw this, I did a chkdsk in Windows and, in fact, the drive did have some issues.  However, it was successfully repaired and chkdsk (and other disk utilities) do not report any further problems from the drive.  I still get the same error when trying to access the drive in Ubuntu however.

One other thing to note - according to the error message, it appears to be trying to mount the partition /dev/sdb2, which does not exist.  Here's my fdsik -l output:
```

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x72d8792f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   117227519    58612736    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7621678e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953523119   976761528+  42  SFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a311

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   204802047   102400000   83  Linux                                                                                                                                                                                
/dev/sdc2       204802048  1953519615   874358784    7  HPFS/NTFS/exFAT                                                                                                                                                                      
                                                                                                                                                                                                                                             
Disk /dev/sdd: 500.1 GB, 500107862016 bytes                                                                                                                                                                                                  
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors                                                                                                                                                                        
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                                                                                       
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                                                                                        
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                                                                            
Disk identifier: 0x7dd50b7b                                                                                                                                                                                                                  
                                                                                                                                                                                                                                             
   Device Boot      Start         End      Blocks   Id  System                                                                                                                                                                               
/dev/sdd1   *        2048      178175       88064    7  HPFS/NTFS/exFAT                                                                                                                                                                      
/dev/sdd2          178176   976769023   488295424    7  HPFS/NTFS/exFAT                                                                                                                                                                      
                                                                                                                                                                                                                                             
Disk /dev/sde: 16.0 GB, 16001269760 bytes                                                                                                                                                                                                    
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors                                                                                                                                                                          
Units = sectors of 1 * 512 = 512 bytes                                                                                                                                                                                                       
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                                                                                                                        
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                                                                                                                            
Disk identifier: 0xc3072e18  
```So /dev/sdb2 doesn't even exist.  When I try to mount /dev/sdb1 though, with:

```
sudo mount -t ntfs /dev/sdb1 /media/orion/Storage\ II
```I get the following error:

```
ntfs_mst_post_read_fixup_warn: magic: 0xba010000  size: 1024   usa_ofs: 11076  usa_count: 1059: Invalid argument                                                                                                                             
Record 0 has no FILE magic (0xba010000)                                                                                                                                                                                                      
Failed to load $MFT: Input/output error                                                                                                                                                                                                      
Failed to mount '/dev/sdb1': Input/output error                                                                                                                                                                                              
NTFS is either inconsistent, or there is a hardware fault, or it's a                                                                                                                                                                         
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows                                                                                                                                                                       
then reboot into Windows twice. The usage of the /f parameter is very                                                                                                                                                                        
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```So it looks like there may still be a problem on the disk that Ubuntu finds but Windows doesn't.  Any suggestions?  Thanks very much.

---

### Post by gnush on 2012-12-30
> In the first case run chkdsk /f on Windows                                                                                                                                                                        then reboot into Windows twice. The usage of the /f parameter is very                                                                                                                                                                         important!Did you do this? If you did, I really have no idea. Is there anything important on the partition?

---

### Post by Ørion on 2012-12-30
> **gnush said:**
> Did you do this? If you did, I really have no idea. Is there anything important on the partition?

Yup.  The first time it found errors and repaired them, and I've run it several times since with no errors detected.  The drive has a lot of data that would be annoying to replace, but nothing I can't live without.  I guess I should add that I can access the drive with no problem from Windows.

---

### Post by vanadium on 2012-12-30
This thread sheds some light on your issue: [http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)

You appear to be dealing with a "Dynamic disk", which is a disk partitionned according to a proprietary MS Windows format.

Here a number of options are listed to convert the volume to a traditional format: [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by Ørion on 2012-12-30
> **vanadium said:**
> This thread sheds some light on your issue: [http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)

You appear to be dealing with a "Dynamic disk", which is a disk partitionned according to a proprietary MS Windows format.

Here a number of options are listed to convert the volume to a traditional format: [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)


That's definitely the problem, thanks.  Looks like the only thing for me to do is backup, reformat, and restore.  Oh well.  Thanks so much for your help.

---

