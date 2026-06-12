---
title: "recover raid 5 array"
date: 2011-11-18
forum: Hardware
---

### Post by razrline on 2011-11-18
I have a software (mdadm) raid 5 array with (3) 3TB drives, all GPT and all formatted NTFS (the idea was to make it compatible with Windows, which isn't possible). These are purely data drives. I upgraded my boot drive and haven't been able to mount the array since. It assembles just fine, shows 3 drives all in sync, all with persistent superblocks. I can fail the recovery drive and add it back and it sync up fine. They all read as NTFS to gparted. When I try and mount the array, though, I get an ntfs-3g error that the array has no superblock and that the filesystem is inconsistent. Gparted shows the /dev/md0 but registers it as unallocated. 
    I haven't use mdadm --create out of fear it would format the drives, and can't use mdadm --build on a raid5. fdisk is useless on drives this size. Thanks to mdadm chkdsk is useless as windows won't see the raid array. Parted won't properly handle ntfs drives. Ntfsfix gives a 'Bad Magic' error. At this point I just need to access the data on the drives (have an extra 6 TB to copy them to) but when I mount the drives individually I only get their raid mount folders.
   Will reboot with specific mount and ntfsfix error responses.

---

### Post by razrline on 2011-11-18
--------------MDSTAT results:
cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdc1[1] sdb1[3] sda1[4]
      5860527104 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>


----------- mdadm -E on devices results:
sudo mdadm -E /dev/sd[abc]1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 797fec5c:0513c396:f60051ab:c97d884b
           Name : smizmar:0  (local to host smizmar)
  Creation Time : Tue Jul 12 19:34:47 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 11721054208 (5589.03 GiB 6001.18 GB)
  Used Dev Size : 5860527104 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 03ad01cd:b13286bd:e6f30b52:e9a76952

    Update Time : Thu Nov 17 21:04:34 2011                                                                                                                       
       Checksum : ce5ce7aa - correct                                                                                                                             
         Events : 338006                                                                                                                                         
                                                                                                                                                                 
         Layout : left-symmetric                                                                                                                                 
     Chunk Size : 512K                                                                                                                                           
                                                                                                                                                                 
   Device Role : Active device 0                                                                                                                                 
   Array State : AAA ('A' == active, '.' == missing)                                                                                                             
/dev/sdb1:                                                                                                                                                       
          Magic : a92b4efc                                                                                                                                       
        Version : 1.2                                                                                                                                            
    Feature Map : 0x0                                                                                                                                            
     Array UUID : 797fec5c:0513c396:f60051ab:c97d884b                                                                                                            
           Name : smizmar:0  (local to host smizmar)                                                                                                             
  Creation Time : Tue Jul 12 19:34:47 2011                                                                                                                       
     Raid Level : raid5                                                                                                                                          
   Raid Devices : 3                                                                                                                                              
                                                                                                                                                                 
 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)                                                                                                            
     Array Size : 11721054208 (5589.03 GiB 6001.18 GB)                                                                                                           
  Used Dev Size : 5860527104 (2794.52 GiB 3000.59 GB)                                                                                                            
    Data Offset : 2048 sectors                                                                                                                                   
   Super Offset : 8 sectors                                                                                                                                      
          State : clean                                                                                                                                          
    Device UUID : 1a8fca29:7791e655:d415f39f:1c130d06

    Update Time : Thu Nov 17 21:04:34 2011
       Checksum : c510b5a6 - correct
         Events : 338006

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 797fec5c:0513c396:f60051ab:c97d884b
           Name : smizmar:0  (local to host smizmar)
  Creation Time : Tue Jul 12 19:34:47 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 5860528128 (2794.52 GiB 3000.59 GB)
     Array Size : 11721054208 (5589.03 GiB 6001.18 GB)
  Used Dev Size : 5860527104 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e951e10c:f0703968:e9618277:bfc3850b

    Update Time : Thu Nov 17 21:04:34 2011
       Checksum : 978254a4 - correct
         Events : 338006

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)

---------------mdadm -E /dev/md0 results:
sudo mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.

----------------mount command results:
ntfs-3g /dev/md0 /media/DOOP
ntfs_mst_post_read_fixup: magic: 0x00000000  size: 1024  usa_ofs: 0  usa_count: 65535: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---------------ntfsfix results:
ntfs-3g /dev/md0 /media/DOOP
ntfs_mst_post_read_fixup: magic: 0x00000000  size: 1024  usa_ofs: 0  usa_count: 65535: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
Failed to mount '/dev/md0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

