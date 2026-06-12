---
title: "Trouble Writing to External Drive"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by gro.utnubu on 2007-08-04
I've read other relevant posts on this but don't know enough to generalize to my problem.  The external is used primarily on a Windows box, where it writes fine, but I can't write to it now.  I installed ntfs-config, which didn't do the job.

permissions are
 dr-x------ 1 xxx  xxx  12288 2007-04-02 12:06 Backup

mount says
 /dev/sda1 on /media/Backup type ntfs (rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)

fstab has nothing, which I've learned is okay because this is a removable disk.

dmesg is verbose on the subject:
[17181296.304000] usb 3-1: new high speed USB device using ehci_hcd and address 16
[17181296.436000] usb 3-1: configuration #1 chosen from 1 choice
[17181296.628000] scsi4 : SCSI emulation for USB Mass Storage devices
[17181296.628000] usb-storage: device found at 16
[17181296.628000] usb-storage: waiting for device to settle before scanning
[17181301.628000] usb-storage: device scan complete
[17181301.628000]   Vendor: ST94011A  Model:                   Rev: 3.05
[17181301.628000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181301.632000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[17181301.632000] sdb: Write Protect is off
[17181301.632000] sdb: Mode Sense: 00 14 00 00
[17181301.632000] sdb: assuming drive cache: write through
[17181301.632000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[17181301.632000] sdb: Write Protect is off
[17181301.632000] sdb: Mode Sense: 00 14 00 00
[17181301.632000] sdb: assuming drive cache: write through
[17181301.632000]  sdb: sdb1
[17181302.060000] sd 4:0:0:0: Attached scsi disk sdb
[17181302.060000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17181302.408000] NTFS-fs warning (device sdb1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17181302.456000] NTFS volume version 3.1.
[17181392.832000] usb 3-1: USB disconnect, address 16
[17181393.076000] usb 3-1: new high speed USB device using ehci_hcd and address 17
[17181393.208000] usb 3-1: configuration #1 chosen from 1 choice
[17181395.444000] usb 3-1: can't set config #1, error -71
[17181395.604000] usb 3-1: USB disconnect, address 17
[17181395.844000] usb 3-1: new high speed USB device using ehci_hcd and address 18
[17181395.976000] usb 3-1: configuration #1 chosen from 1 choice
[17181396.196000] eth0: Autonegotiation advertising 0x5e1  partner 0x45e1.
[17181396.196000] eth0: link up.
[17181399.500000] scsi5 : SCSI emulation for USB Mass Storage devices
[17181399.500000] usb-storage: device found at 18
[17181399.500000] usb-storage: waiting for device to settle before scanning
[17181404.500000] usb-storage: device scan complete
[17181408.656000]   Vendor: ST94011A  Model:                   Rev: 3.05
[17181408.656000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181408.660000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[17181408.660000] sdb: Write Protect is off
[17181408.660000] sdb: Mode Sense: 00 14 00 00
[17181408.660000] sdb: assuming drive cache: write through
[17181408.660000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[17181408.660000] sdb: Write Protect is off
[17181408.660000] sdb: Mode Sense: 00 14 00 00
[17181408.660000] sdb: assuming drive cache: write through
[17181408.660000]  sdb:<6>usb 3-1: reset high speed USB device using ehci_hcd and address 18
[17181439.124000]  sdb1
[17181439.124000] sd 5:0:0:0: Attached scsi disk sdb
[17181439.124000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[17181489.912000] eth0: increased tx threshold, txcfg 0xd0f01004.
[17182022.580000] usb 3-1: USB disconnect, address 18
[17182022.820000] usb 3-1: new high speed USB device using ehci_hcd and address 19
[17182022.952000] usb 3-1: configuration #1 chosen from 1 choice
[17182023.768000] scsi6 : SCSI emulation for USB Mass Storage devices
[17182023.768000] usb-storage: device found at 19
[17182023.768000] usb-storage: waiting for device to settle before scanning
[17182028.768000] usb-storage: device scan complete
[17182028.768000]   Vendor: ST94011A  Model:                   Rev: 3.05
[17182028.768000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182028.772000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17182028.772000] sda: Write Protect is off
[17182028.772000] sda: Mode Sense: 00 14 00 00
[17182028.772000] sda: assuming drive cache: write through
[17182028.772000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[17182028.772000] sda: Write Protect is off
[17182028.772000] sda: Mode Sense: 00 14 00 00
[17182028.772000] sda: assuming drive cache: write through
[17182028.772000]  sda: sda1
[17182029.164000] sd 6:0:0:0: Attached scsi disk sda
[17182029.164000] sd 6:0:0:0: Attached scsi generic sg0 type 0
[17182029.516000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17182029.564000] NTFS volume version 3.1.
[17184355.124000] fuse init (API version 7.6)
[17185579.208000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17185581.192000] NTFS volume version 3.1.

 and someone even suggested fdisk -l, here is the output
Disk /dev/sda1: 39.9 GB, 39999504384 bytes
255 heads, 63 sectors/track, 4862 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


where are mount defaults set besides fstab?  A lot of people reported luck mounting as root, how do I do that?  Is that even the problem?  Thanks lots.

-seth

---

### Post by merlinus on 2007-08-04
Are you booted into ubuntu, and the drive mounted, when running these commands?

sudo fdisk -l is returning some strange things.

Did you try to mount the drive manually?  

-merlin

---

### Post by gro.utnubu on 2007-08-04
>> Did you try to mount the drive manually? 

Doesn't work, but I am missing all those options from before

after entering
sudo mount -t ntfs /dev/sda1 /media/test
and 
sudo mount -t ntfs /dev/sda1 /media/test -o defaults

my error is 
cp: cannot create directory `./Whatevs': Read-only file system

mount says
/dev/sda1 on /media/test type ntfs (rw)

and ls says
dr-x------ 1 root root 12288 2007-04-02 12:06 test


Thanks for responding so Fast!
-seth

---

### Post by merlinus on 2007-08-04
Run these again and post output:

```

sudo fdisk -l
cat /etc/fstab

```

-merlin

---

### Post by gro.utnubu on 2007-08-04
root@xxxbox:/media/test# sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1115     8956206    7  HPFS/NTFS
/dev/hda2            1116        3495    19117350   83  Linux
/dev/hda3            3496        3648     1228972+   5  Extended
/dev/hda5            3496        3648     1228941   82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4863    39062016    7  HPFS/NTFS
root@xxxbox:/media/test# cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
root@xxxbox:/media/test#

---

### Post by gro.utnubu on 2007-08-04
and here is cat /etc/mtab

/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-12-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hda1 /media/hda1 fuse rw,nosuid,nodev,noatime,allow_other 0 0
/dev/sda1 /media/test ntfs rw 0 0


also, from before, yes im booted into ubuntu, on edgy, just upgrading now to feisty

-seth

---

### Post by merlinus on 2007-08-04
After you finish upgrading, reboot and post results of the two commands again.

You will almost certainly find that things have changed.

-merlin

---

### Post by gro.utnubu on 2007-08-04
I'm on 56 k, so itll take a day.  

thanks for you help up till now
-seth

---

### Post by pbcartwright on 2007-08-05
I got a 500Gb external USB drive. I followed instructions I found and formatted it ext3. It can be written to in windows & linux. The key in putting it in fstab is the last field, make it a ZERO so it doesn't try to fsck it when you don't have it mounted.
here is my fstab entry:

/dev/sdf5            /media/backup        ext3       acl,user_xattr        1 0

here are the instructions for formatting the drive:
[http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561](http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561)

---

### Post by gro.utnubu on 2007-08-06
After the upgrade to Feisty I still have the same problems, can't write to the external:


 sudo fdisk -l /dev/sda1

Disk /dev/sda1: 39.9 GB, 39999504384 bytes
255 heads, 63 sectors/track, 4862 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sda1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


cat /etc/mtab | grep sda

/dev/sda1 /media/Backup_ ntfs rw,nosuid,nodev,umask=222,utf8 0 0


and the last of dmesg is

[  123.176000] usb 3-1: configuration #1 chosen from 1 choice
[  123.488000] usbcore: registered new interface driver libusual
[  123.552000] Initializing USB Mass Storage driver...
[  123.644000] scsi0 : SCSI emulation for USB Mass Storage devices
[  123.644000] usb-storage: device found at 8
[  123.644000] usb-storage: waiting for device to settle before scanning
[  123.644000] usbcore: registered new interface driver usb-storage
[  123.644000] USB Mass Storage support registered.
[  128.644000] usb-storage: device scan complete
[  128.644000] scsi 0:0:0:0: Direct-Access     ST94011A                  3.05 PQ: 0 ANSI: 0 CCS
[  128.772000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[  128.772000] sda: Write Protect is off
[  128.772000] sda: Mode Sense: 00 14 00 00
[  128.772000] sda: assuming drive cache: write through
[  128.776000] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[  128.776000] sda: Write Protect is off
[  128.776000] sda: Mode Sense: 00 14 00 00
[  128.776000] sda: assuming drive cache: write through
[  128.776000]  sda: sda1
[  129.228000] sd 0:0:0:0: Attached scsi disk sda
[  129.256000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  129.712000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  129.716000] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  129.812000] NTFS volume version 3.1.

And thanks for the link Cartwright, but the drive isn't mine, so I'm not allowed to format it.

mounting manually gives the same return for fdisk and this on mtab:
cat /etc/mtab | grep sda
/dev/sda1 /media/test ntfs rw 0 0


Any leads, I'm not averse to doing my own work, I just don't know where to go.  at all.

Thanks much
-seth

---

