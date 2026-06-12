---
title: "Unable to Mount GPT Partition"
date: 2013-09-20
forum: Hardware
---

### Post by Sathane on 2013-09-20
Hi,

New to the forums but have been working with Linux for a few years now.

I'm stumped on this one.  A client has a 500GB external HD which she has been using for some time and now won't come up properly on her system.  She originally formatted it with her Mac laptop.  She says is wasn't dropped or anything and the drive does spin up but I am unable to mount the proper partition in order to view/recover her data.

Here is the output of "parted /dev/sdd print":

> 
Model: Seagate FreeAgent GoFlex (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                    Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition    boot
 2      210MB   500GB  500GB               FreeAgent GoFlex Drive


I'm not seeing an actual filesystem type for the data partition so attempting to mount it results in the mount command complaining that the partition type needs to be specified.  I've tried mounting with NTFs and HFS+ but neither work.

Can someone point me in the right direction?

Thanks.

Edit:  Decided to see what gdisk says about the drive.  Here is what I get:

> 
Partition number (1-2): 2
Partition GUID code: 48465300-0000-11AA-AA11-00306543ECAC (Apple HFS/HFS+)
Partition unique GUID: 0D6116BB-EB46-444A-91FC-10A7D8351599
First sector: 409640 (at 200.0 MiB)
Last sector: 976510983 (at 465.6 GiB)
Partition size: 976101344 sectors (465.4 GiB)
Attribute flags: 0000000000000000
Partition name: 'FreeAgent GoFlex Drive'

Command (? for help): p
Disk /dev/sdd: 976773167 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0DB43EA3-A5E2-4C82-9B4B-68666CA6D782
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773133
Partitions will be aligned on 8-sector boundaries
Total free space is 262156 sectors (128.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              40          409639   200.0 MiB   EF00  EFI System Partition
   2          409640       976510983   465.4 GiB   AF00  FreeAgent GoFlex Drive

Command (? for help):


So, I'm thinking I can just set the partition type to Apple HFS+ in gdisk but I don't want to do this unless I can be sure that the data on this drive won't be destroyed.

---

### Post by Sathane on 2013-09-20
By the way, trying to mount the drive with "mount -t hfsplus /dev/sdd2 /mnt/usbtmp" fails with:

> 
root@MTS-Archive01:/mnt # mount /dev/sdd2 -t hfsplus -o rw /mnt/usbtmp/
mount: wrong fs type, bad option, bad superblock on /dev/sdd2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


When I run dmesg, I see this:
> 
[ 3554.548211] hfs: unable to find HFS+ superblock


---

### Post by oldfred on 2013-09-20
Your gdisk says af00 which is hfs.

But some info from google says the drives are formatted NTFS from factory.

---

### Post by Sathane on 2013-09-20
That's correct (AF00=HFS/HFS+), however, the parted partition print output says the partition is unlabelled.  I'm thinking this inconsistency is causing part of the problem here.  Also, when I run fsck.hfsplus /dev/sdd2 I just get "** /dev/sdd2" as the output with no actual testing information.

When I use the -q option I get this:

> 
root@MTS-Archive01:/mnt # fsck.hfsplus -q /dev/sdd2
** /dev/sdd2
QUICKCHECK ONLY; NO HFS SIGNATURE FOUND


So, another program that says there is no HFS Signature despite gdisk having it labelled as AF00.

Is there any way to restore that HFS signature so it is seen properly without destroying any data that might be int he partition?

---

### Post by Sathane on 2013-09-20
Running blkid gives me nothing for /dev/sdd2 as well:

```

root@MTS-Archive01:/mnt # blkid /dev/sdd2
root@MTS-Archive01:/mnt # blkid /dev/sdd1
/dev/sdd1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat"

```

---

### Post by oldfred on 2013-09-20
If gdisk is seeing it as hfs then the partition table has it that way, but internal data is not by errors on mounting.

What does testdisk say. It will work with gpt drives as UEFI or efi.

---

### Post by Sathane on 2013-09-20
Trying that tool now.

I ran it and selected the drive.  I didn't get a full partition table output when I selected "Mac [Apple partition map]" for the partition table type so I backed up and selected "[EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)" instead.

I now go to "[Advanced] Filesystem Tools" 

> 
Disk /dev/sdd - 500 GB / 465 GiB - CHS 60801 255 63

     Partition                  Start        End    Size in sectors
  1 P EFI System                    40     409639     409600 [EFI System Partiti
> 2 P Mac HFS                   409640  976510983  976101344 [FreeAgent GoFlex D
rive]

 [  Type  ]  [Superblock] >[Image Creation]  [  Quit  ]


Selecting "Superblock" gives me this:

> 
Disk /dev/sdd - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 2 P Mac HFS                   409640  976510983  976101344 [FreeAgent GoFlex Dr
ive]
Volume header
Bad

Backup volume header
Bad

Sectors are identical.


I'm not sure if I should select the "Dump" option at this point.

I tried running an Imaging process to /dev/sdc2, a second drive I have hooked to this Linux system that I was going to dd the problematic drive to.  I already duplicated the partition structure earlier so I was just backing up the partition to the drive in case I broke something.  That finished way too fast to actually be doing anything - the same result as when I attempted the dd earlier.

Right now I have it running an Analyze on the drive.  It's got 60800 cylinders to process so this will take a bit of time.  Here is what it shows now:

> 
Disk /dev/sdd - 500 GB / 465 GiB - CHS 60801 255 63
Analyse cylinder   394/60800: 00%

check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: Incorrect number of heads/cylinder 16 (FAT) != 255 (HD)
Warning: Incorrect number of sectors per track 32 (FAT) != 63 (HD)
  EFI System                    40     409639     409600 [EFI]


---

### Post by oldfred on 2013-09-20
I do not know MACs. But is there a tool like chkdsk, or fsck for HFS?

---

