---
title: "Sata disk gets put to read only after a while when i boot"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by mbirkis on 2005-11-04
don't understand this!!
when i boot it works fine, then after a while i get that sda2 (the /) partition is read only, the other partitions work fine... i don't understand!!!! :( 

All help appreciated...

error message from dmesg:
[25430.359022] hw tcp v4 csum failed
[25677.120017] hw tcp v4 csum failed
[25962.668481] hw tcp v4 csum failed
[26140.902676] hw tcp v4 csum failed
[26178.420055] hw tcp v4 csum failed
[26182.254754] hw tcp v4 csum failed
[28203.238605] hw tcp v4 csum failed
[28313.581198] hw tcp v4 csum failed
[28313.614662] hw tcp v4 csum failed
[28313.707088] hw tcp v4 csum failed
[28317.544547] hw tcp v4 csum failed
[28318.904320] hw tcp v4 csum failed
[28321.416171] hw tcp v4 csum failed
[28321.505412] hw tcp v4 csum failed
[28325.177937] hw tcp v4 csum failed
[28330.925747] hw tcp v4 csum failed
[28331.015142] hw tcp v4 csum failed
[28331.934036] hw tcp v4 csum failed
[28331.951218] hw tcp v4 csum failed
[28335.178400] hw tcp v4 csum failed
[28335.276607] hw tcp v4 csum failed
[28339.240121] printk: 1 messages suppressed.
[28339.240126] hw tcp v4 csum failed
[28344.481889] printk: 2 messages suppressed.
[28344.481894] hw tcp v4 csum failed
[28350.266901] printk: 3 messages suppressed.
[28350.266905] hw tcp v4 csum failed
[28356.432019] printk: 2 messages suppressed.
[28356.432024] hw tcp v4 csum failed
[28361.818203] hw tcp v4 csum failed
[28370.000483] hw tcp v4 csum failed
[28377.088614] hw tcp v4 csum failed
[28382.571844] hw tcp v4 csum failed
[28385.813834] hw tcp v4 csum failed
[28392.788451] hw tcp v4 csum failed
[28397.875276] hw tcp v4 csum failed
[28416.168192] hw tcp v4 csum failed
[28421.728335] hw tcp v4 csum failed
[28428.720150] hw tcp v4 csum failed
[28433.703191] hw tcp v4 csum failed
[28439.951005] hw tcp v4 csum failed
[28447.897727] hw tcp v4 csum failed
[28655.425716] ata1: translated ATA stat/err 0x35/00 to SCSI SK/ASC/ASCQ 0x4/00/00
[28655.425723] ata1: status=0x35 { DeviceFault SeekComplete CorrectedError Error }
[28655.425735] SCSI error : <0 0 0 0> return code = 0x8000002
[28655.425738] sda: Current: sense key: Hardware Error
[28655.425742]     Additional sense: No additional sense information
[28655.425747] end_request: I/O error, dev sda, sector 32884104
[28655.427425] Aborting journal on device sda2.
[28655.427589] ext3_abort called.
[28655.427592] EXT3-fs error (device sda2): ext3_journal_start_sb: Detected aborted journal
[28655.427596] Remounting filesystem read-only
[28747.511077] hw tcp v4 csum failed

_fdisk -l _
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2040    16386268+   7  HPFS/NTFS
/dev/sda2            2041        3837    14434402+  83  Linux
/dev/sda3            3838        3968     1052257+  82  Linux swap / Solaris
/dev/sda4            3969       19457   124415392+   f  W95 Ext'd (LBA)
/dev/sda5            3969       19457   124415361   83  Linux

_mount_
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-amd64-generic/volatile type tmpfs (rw,mode=0755)
/dev/sda5 on /home type ext3 (rw)
/dev/hdb1 on /home/musikk type ext3 (rw)
/dev/sda1 on /media/sda1 type ntfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

---

