---
title: "Sata Hdd case auto disconnects"
date: 2012-09-21
forum: Hardware
---

### Post by skarosg3 on 2012-09-21
Hi all,
I have a small problem. i got a case for my old 2.5' sata hdd, but when i connect it to my 11.04 I am getting this on system log:
```
usb 1-5: USB disconnect, address 9
 sd 6:0:0:0: Device offlined - not ready after error recovery
 sd 6:0:0:0: [sdc] Unhandled error code
 sd 6:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
 sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 18 dc 90 00 00 f0 00
 end_request: I/O error, dev sdc, sector 1629328
 quiet_error: 6 callbacks suppressed
 Buffer I/O error on device sdc3, logical block 203410
 Buffer I/O error on device sdc3, logical block 203411
 Buffer I/O error on device sdc3, logical block 203412
 Buffer I/O error on device sdc3, logical block 203413
 Buffer I/O error on device sdc3, logical block 203414
 Buffer I/O error on device sdc3, logical block 203415
 Buffer I/O error on device sdc3, logical block 203416
 Buffer I/O error on device sdc3, logical block 203417
 Buffer I/O error on device sdc3, logical block 203418
 Buffer I/O error on device sdc3, logical block 203419
 sd 6:0:0:0: [sdc] Unhandled error code
 sd 6:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
 sd 6:0:0:0: [sdc] CDB: Read(10): 28 00 00 18 dd 80 00 00 10 00
 end_request: I/O error, dev sdc, sector 1629568
```
any ideas what the problem might be and how to fix it.

I have tried it on my win7 netbook and it seems to be working fine.

thanks, ilias

---

### Post by tomgobravo on 2012-09-23
Does your drive mount? I'm having a problem with a disk that works internally but when connected through a SATA-USB adapter it only works for a few seconds to minutes before consistently reporting errors. I won't threadjack with my specifics if your problem is very different. What have you tried to debug or work around this problem?

---

### Post by tomgobravo on 2012-09-24
I've made a bit of progress. Following the replies in  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012291](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1012291) I installed a mainline kernel (hardest step is working out which you need). My disconnect doesn't reproduce as consistently after a switched from "3.2.0-30-generic #48-Ubuntu" to "3.2.27-030227-generic #201208101235" which is a mixed blessing. I also found [https://wiki.ubuntu.com/Kernel/Debugging/USB](https://wiki.ubuntu.com/Kernel/Debugging/USB) which shows more details but needs someone more familiar with USB to make any sense of it.

---

### Post by skarosg3 on 2012-10-02
Hi tomgobravo
thanks for your info.
i will see if your solution works with my problem.
I got a new problem now though. i will ask it here in case someone migh help me. 

while i was copying some files to the external drive, it crashed, and it crashed big time! i had to fore restart it, resulting damaging my internal ntfs drive. For some reason, it changed the file system from ntfs to RAW!! now i cant even use check disk under windows! any idea? 
under ubuntu i cant mount, using gparted i see it as empty, and under windows it tells me that the drive needs formating!

I guess it is a lost cause, and needs to format it in order to make it working, if that would fix anything and i wont have to get a new drive!

---

### Post by westie457 on 2012-10-02
> while i was copying some files to the external drive, it crashed, and it crashed big time! i had to fore restart it, resulting damaging my internal ntfs drive. For some reason, it changed the file system from ntfs to RAW!! now i cant even use check disk under windows! any idea? 
under ubuntu i cant mount, using gparted i see it as empty, and under windows it tells me that the drive needs formating!

I guess it is a lost cause, and needs to format it in order to make it working, if that would fix anything and i wont have to get a new drive!

Before doing anything drastic take a look at testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It might be able to recover the partition table for you.

It can be installed and run from a LiveCD and testdisk is in the repo's.

If it does work then we can sort the other issue.

---

### Post by skarosg3 on 2012-10-02
Thanks for the tip, i tried this, but i am not sure what to do next.
I got to the point where it is doing the quick search, but at the end of it all i was getting was this:
```
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors


Keys A: add partition, L: load backup, Enter: to continue

```

do you know what A and L do?
I chose to continue and now i am doing a deeper search, but i think that i will stop it and redo it tomorrow from scratch, it is getting late, the quick search took more than 2 hours to finish, now with deeper search who knows.

if you could tell me what the other two options do, i might give it a try tomorrow.

thanks though. it seems that the drive is cooked, but the program is good.

edit:
for some reason the log file was updated after i made my choice. this is from the log file:
```

search_part()
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63
file_pread(5,16,buffer,6291519(391/160/25)) read err: Partial read
file_pread(5,16,buffer,6291535(391/160/41)) read err: Input/output error
file_pread(5,1,buffer,6291535(391/160/41)) read err: Input/output error
file_pread(5,16,buffer,436132620(27148/0/1)) read err: Input/output error
file_pread(5,1,buffer,436132620(27148/0/1)) read err: Input/output error
file_pread(5,8,buffer,436132628(27148/0/9)) read err: Input/output error
file_pread(5,3,buffer,436132636(27148/0/17)) read err: Input/output error
file_pread(5,16,buffer,489934321(30497/0/17)) read err: Partial read
file_pread(5,16,buffer,624117776(38849/136/24)) read err: Partial read
file_pread(5,16,buffer,624117823(38849/137/8)) read err: Input/output error
file_pread(5,1,buffer,624117823(38849/137/8)) read err: Input/output error

Results

interface_write()
 
No partition found or selected for recovery
```

---

### Post by westie457 on 2012-10-02
I think you might be right about the drive being cooked however there might still be a chance of recovering it.

Was/is there anything on the drive of importance to you?
If yes try photorec (comes with testdisk)to recover the files. Any found will have to be written to a different drive, this will take a while to find the files and they will be recovered without any name information, only numbers and the extension.

Another option is to connect the drive directly to a computer and boot using a LiveCD. Then run Disk Utility to run a S.M.A.R.T. test on the drive. Post the results here for a considered opinion.
In fact I would try the above option before running photorec.

If there is nothing on the drive to worry about you could try zeroing out the drive using ```
dd if=/dev/zero of=dev/sdb
```where sdb is the 'cooked' drive. Edit the command to suit.

[COLOR="Red"]Double check before hitting enter[/COLOR] or you could wipe the wrong one.  See ```
man dd
```for more info.

If I remember rightly the dd command will stop if the MBR of the drive cannot be written to, though TBH I am not sure on the last part. Hope this has not frightened you too much and is of some help.

---

### Post by skarosg3 on 2012-10-03
It worked!!
I am not sure what combination of options i chose but when i was done with it (I wasnt sure that it worked at the time) i went into windows and it auto checkdisk it at boot time, and now it is working great!
well, almost great since it doesnt auto mount (i think it changed the name of the drive and doesnt recognise the old name) that i will fix it at later time. i think i had this problem at the past and managed to solve it somehow.

now, with my older problem, i will have a look at the links tomgobravo mentioned tomorrow. do you have anything else i might try?

in case this might help anybody else in the future this is the output of the log that eventually got my hdd working!
```

Wed Oct  3 08:32:17 2012
Command line: TestDisk

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.38-15-generic (#66-Ubuntu SMP Tue Aug 14 17:25:35 UTC 2012) i686
Compiler: GCC 4.4
Compilation date: 2011-11-15T02:42:19
ext2fs lib: 1.41.9, ntfs lib: libntfs-3g, reiserfs lib: 0.3.1-rc8, ewf lib: 20100226
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: native_max 976773168 sectors
/dev/sda: dco        976773168 sectors
/dev/sdb: LBA, HPA, DCO support
/dev/sdb: size       240121728 sectors
/dev/sdb: user_max   240121728 sectors
/dev/sdb: native_max 240121728 sectors
/dev/sdb: dco        240121728 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - WDC WD5000AAKS-00YGA0, S/N:WD-WCAS80666962, FW:12.01C02
Disk /dev/sdb - 122 GB / 114 GiB - CHS 14946 255 63, sector size=512 - Maxtor 6Y120P0, S/N:Y428XQAE, FW:YAR41BW0

Partition table type (auto): Intel
Disk /dev/sda - 500 GB / 465 GiB - WDC WD5000AAKS-00YGA0
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 1 type 42: no test
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 P W2K Dynamic/SFS          0   1  1 60800 254 63  976768002
No partition is bootable
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
file_pread(4,16,buffer,6291519(391/160/25)) read err: Partial read
file_pread(4,16,buffer,6291535(391/160/41)) read err: Input/output error
file_pread(4,1,buffer,6291535(391/160/41)) read err: Input/output error
file_pread(4,16,buffer,404067022(25152/2/17)) read err: Partial read
file_pread(4,1,buffer,404067024(25152/2/19)) read err: Input/output error
file_pread(4,16,buffer,434133118(27023/136/56)) read err: Input/output error
file_pread(4,16,buffer,489934321(30497/0/17)) read err: Partial read
file_pread(4,16,buffer,624117776(38849/136/24)) read err: Input/output error
file_pread(4,16,buffer,624117823(38849/137/8)) read err: Input/output error
file_pread(4,1,buffer,624117823(38849/137/8)) read err: Input/output error

Results

interface_write()
 
No partition found or selected for recovery
ntfs_mst_post_read_fixup: magic: 0x16f60725  size: 1024  usa_ofs: 45381  usa_count: 42767: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x6f98f57e  size: 1024  usa_ofs: 6458  usa_count: 53774: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x3e1ceecb  size: 1024  usa_ofs: 60487  usa_count: 3060: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x9a1a8123  size: 1024  usa_ofs: 13201  usa_count: 61543: Invalid argument
$MFTMirr error: Invalid mft record for '$MFT'.
ntfs_mst_post_read_fixup: magic: 0x83ca33c3  size: 1024  usa_ofs: 34351  usa_count: 7159: Invalid argument
Record 5 has no FILE magic (0x83ca33c3)

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
file_pread(4,16,buffer,6291519(391/160/25)) read err: Partial read
file_pread(4,16,buffer,411987114(25645/3/1)) read err: Input/output error
file_pread(4,1,buffer,411987114(25645/3/1)) read err: Input/output error
file_pread(4,16,buffer,436132619(27147/254/63)) read err: Input/output error
file_pread(4,1,buffer,436132635(27148/0/16)) read err: Input/output error
file_pread(4,16,buffer,437997119(27264/15/15)) read err: Input/output error
file_pread(4,1,buffer,437997119(27264/15/15)) read err: Input/output error
file_pread(4,16,buffer,543326208(33820/125/34)) read err: Input/output error
file_pread(4,16,buffer,624117823(38849/137/8)) read err: Partial read
file_pread(4,1,buffer,624117824(38849/137/9)) read err: Input/output error
file_pread(4,16,buffer,675958910(42076/126/33)) read err: Partial read
NTFS at 60800/254/63
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS found using backup sector!, 500 GB / 465 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS found using backup sector!, 500 GB / 465 GiB
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.
ntfs_ucstoutf8: iconv_open failed


dir_partition inode=5
   * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS found using backup sector!, 500 GB / 465 GiB
ntfs_dir: ntfs_inode_open failed
Directory /

interface_write()
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS found using backup sector!, 500 GB / 465 GiB
NTFS at 0/1/1
filesystem size           4800649661878086548 976768002
sectors_per_cluster       41 8
mft_lcn                   4144205775 61048000
mftmirr_lcn               968488652 2
clusters_per_mft_record   -62 -10
clusters_per_index_record 81 1
Boot sector
Status: Bad

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
ntfs_mst_post_read_fixup: magic: 0x16f60725  size: 1024  usa_ofs: 45381  usa_count: 42767: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x6f98f57e  size: 1024  usa_ofs: 6458  usa_count: 53774: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x3e1ceecb  size: 1024  usa_ofs: 60487  usa_count: 3060: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x9a1a8123  size: 1024  usa_ofs: 13201  usa_count: 61543: Invalid argument
$MFTMirr error: Invalid mft record for '$MFT'.
ntfs_mst_post_read_fixup: magic: 0x83ca33c3  size: 1024  usa_ofs: 34351  usa_count: 7159: Invalid argument
Record 5 has no FILE magic (0x83ca33c3)
rebuild_NTFS_BS
mft at 488384000, seq=1, main=0 res=1
ntfs_find_mft: mft_lcn             61048000
ntfs_find_mft: mftmirr_lcn         2
ntfs_find_mft: sectors_per_cluster 8
ntfs_find_mft: mft_lcn             61048000
ntfs_find_mft: mftmirr_lcn         2
ntfs_find_mft: mft_record_size     1024
ntfs_find_mft: index_block_size    4096
             New / Current boot sector
filesystem size           976768002 4800649661878086548
sectors_per_cluster       8 41
mft_lcn                   61048000 4144205775
mftmirr_lcn               2 968488652
clusters_per_mft_record   -10 -62
clusters_per_index_record 1 81
Extrapolated boot sector and current boot sector are different.
filesystem size           976768002 4800649661878086548
sectors_per_cluster       8 41
mft_lcn                   61048000 4144205775
mftmirr_lcn               2 968488652
clusters_per_mft_record   -10 -62
clusters_per_index_record 1 81
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.
ntfs_ucstoutf8: iconv_open failed

ntfs_dir: ntfs_inode_open failed
Directory /
filesystem size           976768002 4800649661878086548
sectors_per_cluster       8 41
mft_lcn                   61048000 4144205775
mftmirr_lcn               2 968488652
clusters_per_mft_record   -10 -62
clusters_per_index_record 1 81
Write new boot!

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS found using backup sector!, 500 GB / 465 GiB
NTFS at 0/1/1
NTFS at 0/1/1
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
ntfs_mst_post_read_fixup: magic: 0x4874f1d4  size: 1024  usa_ofs: 33801  usa_count: 42269: Invalid argument
Record 6 has no FILE magic (0x4874f1d4)
Failed to open inode FILE_Bitmap: Input/output error
ntfs_mst_post_read_fixup: magic: 0x83ca33c3  size: 1024  usa_ofs: 34351  usa_count: 7159: Invalid argument
Record 5 has no FILE magic (0x83ca33c3)
ntfs_mst_post_read_fixup: magic: 0x16f60725  size: 1024  usa_ofs: 45381  usa_count: 42767: Invalid argument
Record 0 has no FILE magic (0x16f60725)
Failed to load $MFT: Input/output error
ntfs_mst_post_read_fixup: magic: 0x16f60725  size: 1024  usa_ofs: 45381  usa_count: 42767: Invalid argument
Record 0 has no FILE magic (0x16f60725)
Failed to load $MFT: Input/output error
repair_MFT
NTFS at 0/1/1
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.
ntfs_ucstoutf8: iconv_open failed
ntfs_dir: ntfs_inode_open failed
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
MFT and MFT mirror are bad. Failed to repair them.
MFT and MFT mirror are bad. Failed to repair them.

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS, 500 GB / 465 GiB
NTFS at 0/1/1
NTFS at 0/1/1
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
rebuild_NTFS_BS
mft at 488384000, seq=1, main=0 res=1
ntfs_find_mft: mft_lcn             61048000
ntfs_find_mft: mftmirr_lcn         2
ntfs_find_mft: sectors_per_cluster 8
ntfs_find_mft: mft_lcn             61048000
ntfs_find_mft: mftmirr_lcn         2
ntfs_find_mft: mft_record_size     1024
ntfs_find_mft: index_block_size    4096
Extrapolated boot sector and current boot sector are identical.
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     Rebuild Boot sector           Boot sector
0000 3cc0464e 54465320   <.FNTFS   3cc0464e 54465320   <.FNTFS 
0008 20202000 02080000      .....  20202000 02080000      .....
0010 00000000 00f80000   ........  00000000 00f80000   ........
0018 3f00ff00 3f000000   ?...?...  3f00ff00 3f000000   ?...?...
0020 00000000 b3b29ddb   ........  00000000 b3b29ddb   ........
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.
ntfs_ucstoutf8: iconv_open failed

ntfs_dir: ntfs_inode_open failed
Directory /
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS, 500 GB / 465 GiB
NTFS at 0/1/1
NTFS at 0/1/1
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
ntfs_mst_post_read_fixup: magic: 0x4874f1d4  size: 1024  usa_ofs: 33801  usa_count: 42269: Invalid argument
Record 6 has no FILE magic (0x4874f1d4)
Failed to open inode FILE_Bitmap: Input/output error
ntfs_mst_post_read_fixup: magic: 0x83ca33c3  size: 1024  usa_ofs: 34351  usa_count: 7159: Invalid argument
Record 5 has no FILE magic (0x83ca33c3)
ntfs_mst_post_read_fixup: magic: 0x16f60725  size: 1024  usa_ofs: 45381  usa_count: 42767: Invalid argument
Record 0 has no FILE magic (0x16f60725)
Failed to load $MFT: Input/output error
ntfs_mst_post_read_fixup: magic: 0x16f60725  size: 1024  usa_ofs: 45381  usa_count: 42767: Invalid argument
Record 0 has no FILE magic (0x16f60725)
Failed to load $MFT: Input/output error
repair_MFT
NTFS at 0/1/1
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.
ntfs_ucstoutf8: iconv_open failed
ntfs_dir: ntfs_inode_open failed
ntfs_device_testdisk_io_ioctl() unimplemented
ntfs_device_testdisk_io_ioctl() unimplemented
MFT and MFT mirror are bad. Failed to repair them.
MFT and MFT mirror are bad. Failed to repair them.

ntfs_boot_sector
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [New_Volume]
     NTFS, 500 GB / 465 GiB
NTFS at 0/1/1
NTFS at 0/1/1
filesystem size           976768002
sectors_per_cluster       8
mft_lcn                   61048000
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
You will have to reboot for the change to take effect.

TestDisk exited normally.
```

---

### Post by westie457 on 2012-10-03
Glad you got it working without doing any of those potentially dangerous suggestions.

To get the drive to auto-mount I do khnow that fstab has to be edited, however I am totally unsure of the procedure so am not going to make suggestions for it. Possibly oldfred will happen across this thread and point you in the right direction.

---

### Post by skarosg3 on 2012-10-04
Yes, it was fstab.
for some reason it changed the ID of the drive. changed it back and it auto mounts just fine.
earlier you said:
> **westie457 said:**
> 
If it does work then we can sort the other issue.
what did you had in mind?

---

### Post by westie457 on 2012-10-04
If I remember correctly the first issue was the drive being disconnected (guessing you meant unmounted) from the system. Then you had a potentially disastrous for you situation, which is roughly where I came in. At that time I was concerned only with rescuing the drive and the information on it.

To me it looks like that issue has been resolved. Does the drive still get disconnected?

---

### Post by skarosg3 on 2012-10-04
Yes, as the topic suggest, my first problem was that my external hdd sata case is being unmounted. this (i guess) caused my other problem of crushing my internal hd.
from what you said on your first post here, i figured that you meant that we should first solve the crashed hd and then we can sort out the other issue, that of the unmounting hd.
Sorry if i misunderstood.

---

