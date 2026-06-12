---
title: "How safe to repair an ipod vfat? Q for a HW guru"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by pepster on 2008-02-04
My ipod video has been acting up. At first I thought I lost all my songs as it suddenly "forgot" 6000 songs. I was able to retrieve them via gtkpod, but the ipod would not automount anymore and is not recognized as an ipod. Manually mounting and running 
  sck.vfat -n  -l /dev/sdc2

Gives stuff as shown below. The question is how safe it is to let sck.vfat repair the filesystem, as I am unsure if there is any APPLE magic in there? The magic numbers are especially of interest. any help will be greatly appreciated.

Thanks, Joseph

FSINFO sector has bad magic number(s):
  Offset 0: 0xc161d252 != expected 0x41615252
  Offset 484: 0xe141f272 != expected 0x61417272
  Auto-correcting it.

..... 

/iPod_Control/iTunes
  Has a large number of bad entries. (6/14)
  Not dropping it in auto-mode.
/iPod_Control/iTunes/PÌAÙCÏ~±.  
  Bad file name.
  Auto-renaming it.
  Renamed to 000\0000000.\000 
/iPod_Control/iTunes/PÌAÙCÏ~².  
  Bad file name.
  Auto-renaming it.
  Renamed to 001\0000000.\000 
/iPod_Control/iTunes/IÔUÎEÓDÂ.  
  Bad file name.
  Auto-renaming it.
  Renamed to 002\0000000.\000 
/iPod_Control/iTunes/AÐ\000ì\000á\000ù.\000 \000
  Start cluster beyond limit (2154725376 > 14594630). Truncating file.
/iPod_Control/iTunes/AÐ\000ì\000á\000ù.\000 \000
  File size is 4294934528 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/iPod_Control/iTunes/000\0000000.\000 
  Start cluster beyond limit (2158603620 > 14594630). Truncating file.
/iPod_Control/iTunes/000\0000000.\000 
  File size is 2147647772 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/iPod_Control/iTunes/AÐ\000ì\000á\000ù.\000 \000
  Start cluster beyond limit (2154725376 > 14594630). Truncating file.
/iPod_Control/iTunes/AÐ\000ì\000á\000ù.\000 \000
  File size is 4294934528 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/iPod_Control/iTunes/001\0000000.\000 
  Start cluster beyond limit (2158603653 > 14594630). Truncating file.
/iPod_Control/iTunes/001\0000000.\000 
  File size is 2147647772 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/iPod_Control/iTunes/Aé\000Ô\000õ\000î.\000å\000
  Start cluster beyond limit (2147516416 > 14594630). Truncating file.
/iPod_Control/iTunes/Aé\000Ô\000õ\000î.\000å\000
  File size is 4294967295 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/iPod_Control/iTunes/002\0000000.\000 
  Start cluster beyond limit (2158600706 > 14594630). Truncating file.
/iPod_Control/iTunes/002\0000000.\000 
  File size is 2154868888 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Checking file /iPod_Control/Device/.       .  
Checking file /iPod_Control/Device/.(R)      .  
Checking file /iPod_Control/Device/AÓ\000ù\000ó\000É.\000î\000
Checking file /iPod_Control/Device/SÙSÉNÆO .  
Checking file /iPod_Control/Device/AÐ\000ò\000å\000æ.\000å\000
Checking file /iPod_Control/Device/PÒEÆEÒ~±.  
Checking file /iPod_Control/Device/Aã\000ì\000ï\000ã.\000ë\000
Checking file /iPod_Control/Device/CÌOÃK   .  
Checking file /iPod_Control/Device/Aò\000á\000ä\000é.\000ï\000
Checking file /iPod_Control/Device/RÁDÉO   .  
Checking file /iPod_Control/Device/Aß\000ö\000ï\000ì.\000õ\000
Checking file /iPod_Control/Device/_ÖOÌUÍ~±.  
Checking file /iPod_Control/Device/Aã\000ì\000ï\000ã.\000ë\000
Checking file /iPod_Control/Device/CÌOÃK   .  
Checking file /iPod_Control/Device/clock (CLOCK)
Checking file /iPod_Control/Device/SysInfo (SYSINFO)
Checking file /iPod_Control/Device/Preferences (PREFER~1)
Checking file /iPod_Control/Device/radio (RADIO)
/iPod_Control/Device
  Has a large number of bad entries. (14/18)
  Not dropping it in auto-mode.
/iPod_Control/Device/.       .  
  Bad file name.
  Auto-renaming it.
  Renamed to 000\0000000.\000 
/iPod_Control/Device/.(R)      .  
  Bad file name.
  Auto-renaming it.
  Renamed to 001\0000000.\000 
/iPod_Control/Device/SÙSÉNÆO .  
  Bad file name.
  Auto-renaming it.
  Renamed to 002\0000000.\000 
/iPod_Control/Device/PÒEÆEÒ~±.  
  Bad file name.
  Auto-renaming it.
  Renamed to 003\0000000.\000 
/iPod_Control/Device/CÌOÃK   .  
  Bad file name.
  Auto-renaming it.
  Renamed to 004\0000000.\000 
/iPod_Control/Device/RÁDÉO   .  
  Bad file name.
  Auto-renaming it.
  Renamed to 005\0000000.\000 
/iPod_Control/Device/_ÖOÌUÍ~±.  
  Bad file name.
  Auto-renaming it.
  Renamed to 006\0000000.\000 
/iPod_Control/Device/CÌOÃK   .  
  Bad file name.
  Auto-renaming it.
  Renamed to 007\0000000.\000 
/iPod_Control/Device
  "." is missing. Can't fix this yet.
/iPod_Control/Device
  ".." is missing. Can't fix this yet.
/iPod_Control/Device/000\0000000.\000 
  Directory has non-zero size. Fixing it.
/iPod_Control/Device/000\0000000.\000 
  Start cluster beyond limit (2147516421 > 14594630). Truncating file.

---

