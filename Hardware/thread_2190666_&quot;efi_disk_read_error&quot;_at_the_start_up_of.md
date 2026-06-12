---
title: "&quot;efi disk read error&quot; at the start up of Ubuntu 12.04 on HPz420"
date: 2013-11-28
forum: Hardware
---

### Post by janverbesselt on 2013-11-28
Hi,

I am seeing a "efi disk read error" at the start up (i.e. black screen) of Ubuntu 12.04 on new HP z420 workstation. After that Ubuntu successfully boots up. I just freshly installed Ubuntu on a new computer which had nothing installed except DOS. When installing Ubuntu I choose Overwrite existing OS (i.e. DOS) i.e. the most simple option. 

What does this efi disk read error mean and if it is important what can I do about this?
Does it have anything to do with the GPT part on the sda1. If so how can I use gdisk to deal with this?

thanks for your advice,
Jan

Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.8.0-33-generic x86_64)

 
sudo fdisk -l
[sudo] password for verbe039: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x10831082


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x10831083


Disk /dev/sdc doesn't contain a valid partition table


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x10831084

rocessor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 62
model name      : Intel(R) Xeon(R) CPU E5-1680 v2 @ 3.00GHz
stepping        : 4
microcode       : 0x416
cpu MHz         : 1200.000
cache size      : 25600 KB
physical id     : 0
siblings        : 16
core id         : 1
cpu cores       : 8
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes

---

### Post by oldfred on 2013-11-29
Fdisk does not work on gpt partitioned drives. You can use parted or download gdisk which is the fdisk for gpt partitioned drives.

UEFI may be just configured to boot in UEFI mode or wants to boot with the Windows boot file but finally does let you boot with Ubuntu. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by janverbesselt on 2013-11-29
This is the Create BootInfo report:
   [http://paste.ubuntu.com/6494668/](http://paste.ubuntu.com/6494668/)

Thanks for your advice

---

### Post by oldfred on 2013-11-29
I do not  see any real boot issues.
What settings do you have in UEFI/BIOS? It looks like you have installed with the signed kernels, so UEFI secure boot should work, but have you tried with secure boot off, but UEFI on?

I do prefer to use smaller / (root) partitions of 25GB and use rest of drive for data or /home. Then the system files are closer together on drive. Note lines 339 & 340 where files are far apart. 

Are you using RAID on the 3 drives, normally Boot-Repair picks that up, or are they just not configured yet? They do not show any partitions and look like they need to be partitioned. Do not just write data to unpartitioned drives as if they are floppy drives.

---

### Post by janverbesselt on 2013-11-29
ok. In the BIOS under security -> secure bootconfiguration -> we have indeed switched secure boot off (disabled) and also disabled legacy support. Fastboot is also disabled. How do we check the UEFI option and whether it is turned on?

We will now continue with using parted and gdisk to configure the hard drives (3 drives) because they are not configured yet.

---

### Post by janverbesselt on 2013-11-29
ok an update. we have now partitioned the other disks, and want to adjust the root partition (/) to 25Gb. How can we do this?
Here is also an updated report from boot-repair:
[http://paste.ubuntu.com/6494941/](http://paste.ubuntu.com/6494941/)
The 'efi disk read error' still appears before Ubuntu boot up (without any problem). So what does this error message mean and should we do something about this?

Thanks.

---

### Post by oldfred on 2013-11-29
It seems every UEFI is different.
Some have specific switches for secure boot, UEFI and CSM. Others have combined UEFI & CSM boot option when secure boot is off. Or system tries to UEFI boot from efi partition and if not found boots from MBR in CSM mode.
And others have mixtures of switches to give the various combinations.
All systems will only offer to boot secure boot systems with secure boot on. Or standard UEFI or CSM will not work, only those seen as secure boot.

Is your UEFI the most current update from Vendor?

---

### Post by janverbesselt on 2013-11-29
How can we find out if our UEFI is the most current update?  It is a brand new computer HP z420 so things might be quite up to date.

---

### Post by oldfred on 2013-11-29
Even new computers may have an UEFI update. You have to go to HP's site and check by model number. 

The error may just be because it looks for Windows efi file and then works, or do you not have ubuntu as the first boot device in UEFI boot order, so it is saying first choice did not work and then goes to second choice?

This seems to say ubuntu is first in boot order.
 efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0001,0002,0007,0008,0005,0006
Boot0000* ubuntu    HD(1,800,2f000,5149c8c4-68d3-4be7-b161-67639774f171)File(EFIubuntushimx64.efi)
Boot0001* DTO UEFI USB Floppy/CD    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0002* DTO UEFI USB Hard Drive    Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0005* DTO Legacy USB Floppy/CD

But do you have a floppy drive? 
Some have reported issues back with BIOS where a boot device does not exist but BIOS is looking for it, may be similar issue?

You should just be able to use gparted to shrink / (root) partition. You have to use live installer as all partitions have to be unmounted. It may boot swap and with MBR you have to normally unmount it, but with your gpt you may not have to. 

If just using other drives as data, you may want to read this. I like to make every drive bootable, just in case. I originally rotated my newest install between my drives. 
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

But with gpt drives and UEFI, you would need an efi partition at beginning of drive.

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

I know Windows chkdsk fixes PBR partition boot sector issues. Boot script reports a minor issue on start of FAT32 partition. Must be unmounted sudo fsck -t vfat /dev/sda1
or
      
 sudo dosfsck -t -a -w /dev/sda1

---

