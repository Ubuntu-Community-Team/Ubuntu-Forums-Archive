---
title: "Hard Disk usb - gparted and fdisk &gt;&gt; close device failed: Remote I/O error"
date: 2017-08-14
forum: Hardware
---

### Post by fiddybux on 2017-08-14
Hi all,

I have tried various search solutions, but nothing as yet has yielded any results for me, hence my reason to ask here.

I have an external USB hard drive that I want to put Ubuntu onto.

It is an 80GB Lacie (Porche Design) thing with a Toshiba 5400rpm drive inside. It is not SMART compatible.

The drive works perfectly in Windows and Mac; it formats, writes and reads for extended periods without issue.

As soon as I attempt to use gparted or fdisk in Ubuntu (live CD, live USB, gparted live USB, a permanent Ubuntu install - basically everywhere), it throws up a bunch of errors:

/dev/sdb: close device failed: Remote I/O error

I can ignore these errors and get through a disk activity process, but then (obviously) there changes haven't been written or whatever.

Why would the drive work perfectly in Windows and not Linux?

Is there some manufacturer 'block' on using the device outside of Microsoft or Apple environments?

How (if at all) can I use this device to install Linux on?

I've just run badblocks on it (formatted within Windows to NTFS), and I have no errors.

Sigh! Any ideas anyone? Pulling my hair out on this one.

Thanks for any advice in advance.

---

### Post by ajgreeny on 2017-08-14
Have you created partitions on that disk using Windows?

If so they may be dynamic partitions which are totally unusable i Linux.

It may be worth seeing a screenshot from gparted, or what fdisk makes of the disk by running ```
sudo fdisk -l
``` with it attached.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by fiddybux on 2017-08-14
Hi,

Thanks for the reply!

The fdisk output is below:

```
Disk /dev/sdb: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FDDD9FC9-177B-4FC6-86C1-DD0651D79FA8

Device     Start       End   Sectors  Size Type
/dev/sdb1   2048 156301311 156299264 74.5G Microsoft basic data
```

Could it be something to do with "Microsoft basic data" listed for TYPE?

I've also just run badblocks on it from within Ubuntu on another machine:

```
sudo badblocks -s /dev/sdb
```

...I had no errors.

The drive writes and reads fine in Windows and worked for ages on a Mac too (when I had access to one of them).

It will even read and write (as NTFS) within Ubuntu - mounts, unmounts, no problems.:confused:

It's an old drive, but has been cared for. There is no reason it should be dead; especially since it seems to work flawlessly in non-Linux systems.

The drive currently has one large NTFS partitions on it, created within Windows dskmgmr.

I've also tried creating ext4 partitions on it from within Windows using MiniTool Partition Wizard ([https://www.partitionwizard.com](https://www.partitionwizard.com)) - Ubuntu was still throwing up the same errors following trying this.

BTW, I noticed it's mounted at /dev/sdc now instead. :)

Totally stumped now. All I've got left is to try Mint liveUSB and see if there is a difference, although I doubt it.

Your point about the dynamic partition intrigued me, but since it now has one 80GB NTFS partition on it, I can't see how this is the case.

Any further suggestions?

Thanks.

---

### Post by fiddybux on 2017-08-14
Deleted

---

### Post by ajgreeny on 2017-08-14
> Your point about the dynamic partition intrigued me, but since it now has one 80GB NTFS partition on it, I can't see how this is the case.

Any further suggestions?
Not sure what you mean by this, but as you made the partition using Windows >  The drive currently has one large NTFS partitions on it, created within Windows dskmgmr. I think that may be your problem, ie a dynamic partition was created.

To create partitions for use in Linux always use a Linux OS, not Windows; you can leave unallocated space if you are, for example installing Linux, but do not create a partition in Windows and then try to install Linux to it, or use it in Linux as this problem will very likely occur.

I suggest you use Windows to backup any files on that disk, then use gparted in Ubuntu, from a live system if necessary, to create a new partition table and then format the partition you need (NTFS?) in the now unallocated space.  That partition should now be available in both OSs.

---

### Post by oldfred on 2017-08-14
It does not look like dynamic partitions, and must have been created on the Mac as it is gpt partitioned. With gpt dynamic is seen as LDM where MBR is seen as SFS.

I used gpt with BIOS starting in about 2011 and use it on USB flash drives.
The gpt is the standard partitioning scheme used with UEFI or Mac with its EFI.
But with UEFI it has to have an ESP - efi system partition or with BIOS a bios_grub partition for grub to correctly install.

Plugging & unplugging USB drives may change drive device, so you have to check every time before you use any command that uses device like /dev/sdc.

---

### Post by fiddybux on 2017-08-14
Well it has one 80GB NTFS partition, which reads /writes fine in Windows and Ubuntu, so that is what I was trying to say that it probably isn't dynamic partition.

I wish I could partition in Linux, but this error is stopping me. I've tried Mint live, Ubuntu live, gparted live etc. Nothing works.

The only constant in all of this is that I'm using live usb's, rather than optical media.

I strongly suspect that this has nothing to do with why the error presents itself, i.e. that I'm running from a live usb, because the hard drive can't be partitioned from a full hard disk installed version of Ubuntu with no other usb devices connected either.

I want to use the whole 80GB drive as a full install for Ubuntu (not live or persistent live). I just don't get why this drive isn't working within any of the Linux OS's I've tried.

If it is dynamic partition that you mention, how can I force (brute) it somehow, and what should I be looking for with fdisk or whatever tool?

I can't even use fdisk to change type to 20 (Linux). Nothing I've tried works.

Thanks.

---

### Post by oldfred on 2017-08-14
Windows sometimes shows NTFS that still needs chkdsk. I might try that first from Windows.
But usually then Linux NTFS driver will not mount in read/write mode.

Use Windows tools to shrink the NTFS partition and see if then gparted sees the unallocated ok.

You could also see what gdisk says about the drive/partition.

sudo gdisk -l /dev/sdc
And maybe just updating info from gdisk with a w to possibly fix issues.

       sudo gdisk /dev/sdc
Command (? for help):
 launch gdisk, then type x, then type e, then type w to save your changes or if not sure q to quit.

or brute force erase everything, but sure you have correct drive.
 Erase drive
sudo sgdisk -Zo /dev/sdc

See this for details on parameters:
man sgdisk

---

### Post by fiddybux on 2017-08-14
> **oldfred said:**
> Windows sometimes shows NTFS that still needs chkdsk. I might try that first from Windows.
But usually then Linux NTFS driver will not mount in read/write mode.

Use Windows tools to shrink the NTFS partition and see if then gparted sees the unallocated ok.

You could also see what gdisk says about the drive/partition.

sudo gdisk -l /dev/sdc
And maybe just updating info from gdisk with a w to possibly fix issues.

       sudo gdisk /dev/sdc
Command (? for help):
 launch gdisk, then type x, then type e, then type w to save your changes or if not sure q to quit.

or brute force erase everything, but sure you have correct drive.
 Erase drive
sudo sgdisk -Zo /dev/sdc

See this for details on parameters:
man sgdisk

Thanks for these alternatives! I have no need for the NTFS partition - that was just for testing. It can go, and has done now.

I ran both sgdisk operations independently following advice in the man pages for sgdisk:

```
sudo sgdisk -Z /dev/sdb
```

```
sudo sgdisk -o /dev/sdb
```

Operations both successful...apparently.

Then...

```
sudo fdisk /dev/sdb
```

Which shows all clear and no errors:

```
Disk /dev/sdb: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: EFD007A0-48EF-4579-89BE-5D26CB46D349
```

Then...

```
sudo fdisk /dev/sdb
```

Blah, blah make 1 partition for the whole drive...(n)ew, (w)rite, etc.

```
Command (m for help): n
Partition number (1-128, default 1): 
First sector (34-156301454, default 2048): 
Last sector, +sectors or +size{K,M,G,T,P} (2048-156301454, default 156301454): 

Created a new partition 1 of type 'Linux filesystem' and of size 74.5 GiB.

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
**/dev/sdb: close device failed: Remote I/O error**
```

Same old problem.

However, as you suggested - a (w)rite from gdisk:

```
sudo gdisk /dev/sdb
```

...produces this:

```
Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdb.
The operation has completed successfully.
```

Remarkably, no errors!!! At this point I'm getting excited. It's been days going in circles with this issue.

But alas no, gparted still gives me the same error, as does fdisk when I try to write any changes:

```
Error fsyncing/closing /dev/sdb1: Remote I/O error
```

This is a real head-scratcher.

---

### Post by oldfred on 2017-08-14
If you create partitions with gdisk does it work?

If using gpt and BIOS and wanting to install grub you need a bios_grub partition for grub to install in BIOS mode to a gpt partitioned drive. The bios_grub should be 1 or 2MB and is unformatted with bios_grub flag.
If drive may ever be used for UEFI, best to add at least a small 100MB ESP - efi system partition FAT32 with boot flag. I normally add both to all new drives and only now use gpt.

---

### Post by fiddybux on 2017-08-14
> **oldfred said:**
> If you create partitions with gdisk does it work?

If using gpt and BIOS and wanting to install grub you need a bios_grub partition for grub to install in BIOS mode to a gpt partitioned drive. The bios_grub should be 1 or 2MB and is unformatted with bios_grub flag.
If drive may ever be used for UEFI, best to add at least a small 100MB ESP - efi system partition FAT32 with boot flag. I normally add both to all new drives and only now use gpt.

gdisk did seem to successfully create the partitions, yes, and fdisk reports them as being present.

Out of curiosity I decided to run e2fsck on the drive, and it threw up superblock errors, and advised I run:

```
sudo e2fsck -b 32768 /dev/sdb
```

Of course I cancelled this and then added the -p flag, so I didn't have to spam Enter/y on all the errors:

```
sudo e2fsck -p -b 32768 /dev/sdb
```

The drive whirs and seems to be fixing issues. Verbose feedback is telling me so.

But right at the end:

```
Error writing file system info: Remote I/O error
```

But yet, I can load into Windows, format the same drive as NTFS or whatever, load the disk up with files, copy them back off and all is well. Crazy.

In gdisk, I just created these partitions:

```
Command (? for help): p
Disk /dev/sdb: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): E5BFE55E-4EA9-4F07-901D-338EF1AC59B3
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 156301454
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048        41945087   20.0 GiB    8303  Linux x86 root (/)
   2        41945088        46139391   2.0 GiB     8200  Linux swap
   3        46139392       156301454   52.5 GiB    8302  Linux /home
```

No errors on writing, and as you can see they (p)rint back.

Then running:

```
sudo fsck -p /dev/sdb
```

Produces:

```
fsck from util-linux 2.29
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a gpt partition table in /dev/sdb
```

Doesn't seem happy does it? I can run the e2fsck suggested, and it will fix a load of inode errors and so forth, but will fail with the same old Remote I/O error at the end.

gparted (once I click Ignore past all the errors), then looks like this:

[img]http://i77.photobucket.com/albums/j58/fiddybux/Screenshot%20from%202017-08-14%2023-55-44_zpszv2uqfmd.png[/img]

The unknown filesystem errors is most probably because they're not formatted.

Attempting to format with:

```
sudo mkfs -t ext4 -v /dev/sdb1
```

Results in the following output and error regrading 'superblocks':

```
mke2fs 1.43.4 (31-Jan-2017)
fs_types for mke2fs.conf resolution: 'ext4'
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1310720 inodes, 5242880 blocks
262144 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2153775104
160 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Filesystem UUID: f12bfd13-8d19-44f5-b92e-1f3979d949ab
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:        
Warning, had trouble writing out superblocks.
```

Attempting to format sda3 also produces the same superblock error.

Any more suggestions please?

---

### Post by oldfred on 2017-08-14
You need to run fsck on a partition that is ext2, ext3 or ext4, not on a drive.

So I would expect lots of issues with attempting to run fsck on sdb, not sdb1 or sdb3.

If gpt you will need the bios_grub. 
It can be anywhere on drive, but I normally make it second after the ESP.
Unformatted 1 or 2MB with bios_grub flag if gparted, or ef02 if gdisk.

---

### Post by fiddybux on 2017-08-15
Fdisk or gdisk usually suggests a default start sector position the first partition at 2048MB (I know this is 2GB), so could I use some of this for the bios_grub?

I don't know why so much space is needed at the start of the drive. The options say it can be as low as 32MB, so I might try this too.

Can gdisk be used to set bios_grub flag? Expert options?

---

### Post by sudodus on 2017-08-15
Maybe the following tips can help you.

1. Wipe the first megabyte of the USB hard disk drive (leave it without any partition table, only zero bytes at the head end of the drive), which can be done in a safe way with [mkusb](https://help.ubuntu.com/community/mkusb),

2. and then use a tool to help you install

- either a persistent live system, which can be done rather automatically with [mkusb](https://help.ubuntu.com/community/mkusb)

- or install a system like installing into an internal drive (but to this USB hard disk drive), which can be done with the standard installer of the Ubuntu [family] iso files. Things will be much easier, if you remove (disconnect or unplug) the internal drive before starting the installation.

See the following links and links from them,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by fiddybux on 2017-08-15
> **oldfred said:**
> If you create partitions with gdisk does it work?

If using gpt and BIOS and wanting to install grub you need a bios_grub partition for grub to install in BIOS mode to a gpt partitioned drive. The bios_grub should be 1 or 2MB and is unformatted with bios_grub flag.
If drive may ever be used for UEFI, best to add at least a small 100MB ESP - efi system partition FAT32 with boot flag. I normally add both to all new drives and only now use gpt.

I'm writing this from with systemrescueCD live boot.

Re: your last post - such as the below you mean, note the 2MB BIOS partition (type ef02?):

```
gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 156301488 sectors, 74.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 396C2233-62D3-4B98-8D55-E7F1199728EA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 156301454
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            6143   2.0 MiB     EF02  BIOS boot partition
   2            6144        41949183   20.0 GiB    8303  Linux x86 root (/)
   3        41949184        46143487   2.0 GiB     8200  Linux swap
   4        46143488       156301454   52.5 GiB    8302  Linux /home
```

gdisk created these without issue. Where do I go from here so I can avoid the I/O error I've been getting?

Following this I set partition 1 (type ef02) to be legacy BIOS bootable in gdisk expert settings (being sure to (w)rite changes to disk at the end of the process). I trust that this was necessary? The output is as follows:

```
Expert command (? for help): a
Partition number (1-4): 1
Known attributes are:
0: system partition
1: hide from EFI
2: legacy BIOS bootable
60: read-only
62: hidden
63: do not automount

Attribute value is 0000000000000000. Set fields are:
  No fields set

Toggle which attribute field (0-63, 64 or <Enter> to exit): 2
Have enabled the 'legacy BIOS bootable' attribute.
Attribute value is 0000000000000004. Set fields are:
2 (legacy BIOS bootable)
```

I have confirmed partition 1 is legacy BIOS bootable (attribute flag 4), as follows:

```
Command (? for help): i
Partition number (1-4): 1
Partition GUID code: 21686148-6449-6E6F-744E-656564454649 (BIOS boot partition)
Partition unique GUID: 00D9C1D6-B0E4-4064-B4EC-D9A07750DC8C
First sector: 2048 (at 1024.0 KiB)
Last sector: 6143 (at 3.0 MiB)
Partition size: 4096 sectors (2.0 MiB)
Attribute flags: 0000000000000004
Partition name: 'BIOS boot partition'
```

Following all of this, if I run e2fsck on the individual partitions as you suggested I should, I get the following result for sdb2 and sdb4:

```
sudo e2fsck -p /dev/sdb4
/dev/sdb4: recovering journal
e2fsck: Unknown code ____ 251 while recovering journal of /dev/sdb4
e2fsck: unable to set superblock flags on /dev/sdb4


/dev/sdb4: ********** WARNING: Filesystem still has errors **********
```


I don't intent to ever use this drive with any other systems (Ubuntu only, no Win ever), so I gather I don't need to bother with UEFI as you noted.

Thanks.

P.S. Incidentally, before doing all of the above, I formatted the drive to NTFS in Win (one large partition) and ran chkdsk -f on the whole disk. No errors! Kind of at my wits end with this now. I've been at it for days and I'm getting nowhere fast, although on the upside I have learned a lot, so not all bad. I don't want to give up, but I'm close.

---

### Post by fiddybux on 2017-08-15
> **sudodus said:**
> Maybe the following tips can help you.

1. Wipe the first megabyte of the USB hard disk drive (leave it without any partition table, only zero bytes at the head end of the drive), which can be done in a safe way with [mkusb](https://help.ubuntu.com/community/mkusb),

2. and then use a tool to help you install

- either a persistent live system, which can be done rather automatically with [mkusb](https://help.ubuntu.com/community/mkusb)

- or install a system like installing into an internal drive (but to this USB hard disk drive), which can be done with the standard installer of the Ubuntu [family] iso files. Things will be much easier, if you remove (disconnect or unplug) the internal drive before starting the installation.

See the following links and links from them,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

Thanks for your input into this. 

Everything helps!

However, I've tried a short wipe many times now and it results in the same I/O error every time. :mad:

Currently part way through a full wipe with mkusb, but I'm expecting the same I/O error right at the end to be honest.

---

### Post by oldfred on 2017-08-15
I normally use gparted to create my partitions with gpt partitioning.

Did not know gdisk had codes for / & /home all mine are just 8300 when seen from gdisk.
While I am sure it is not an issue you probably are 64 bit and / would be 8304 Linux x86-64 root (/ not 8303, but not related to the errors you are getting.

My suggested fsck has a few more parameters, but not sure that will make any difference.
       To see all the ext4 partitions, should be sdb2 & sdb4.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by fiddybux on 2017-08-15
> **oldfred said:**
> I normally use gparted to create my partitions with gpt partitioning.

Did not know gdisk had codes for / & /home all mine are just 8300 when seen from gdisk.
While I am sure it is not an issue you probably are 64 bit and / would be 8304 Linux x86-64 root (/ not 8303, but not related to the errors you are getting.

My suggested fsck has a few more parameters, but not sure that will make any difference.
       To see all the ext4 partitions, should be sdb2 & sdb4.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

When I come to use mkfs to create ext4 on sdb2 (/) and sdb4 (/home), I now get superblock errors:

```

Writing superblocks and filesystem accounting information:        
Warning, had trouble writing out superblocks.

```

I'm currently running on a live installed system. I think earlier today I was able to format within systemrescuecd, and I didn't get these superblock errors.

If I run your suggested command:

```

sudo e2fsck -C0 -p -f -v /dev/sdb2

```

I get:

```

e2fsck: Bad magic number in super-block while trying to open /dev/sdb2
/dev/sdb2: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

This might be because although the partitions exist, they aren't currently formatted.

I'll boot into systemrescuecd, try formatting in there, and attempt your suggestions again.

Thanks.

---

### Post by fiddybux on 2017-08-15
Okay, so I'm in systemrescuecd and I have been able to successfully format /sdb2 (and /sdb4 as well, although I only posted sdb2 below):

```

root@sysresccd /root % mkfs -t ext4 -v /dev/sdb2
mke2fs 1.43.3 (04-Sep-2016)
fs_types for mke2fs.conf resolution: 'ext4'
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1310720 inodes, 5242880 blocks
262144 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2153775104
160 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Filesystem UUID: 5dd548d3-c06f-4b29-a4e2-9d198324ebe3
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done   

```

Why it is that I don't get a superblock error with systemrescuecd and yet I do with my full Ubuntu install is beyond me!!?

Now if I run your suggested command (no sudo needed here are I su'd at the top of the terminal):

```

e2fsck -C0 -p -f -v /dev/sdb2

```

I get:

```

root@sysresccd /root % e2fsck -C0 -p -f -v /dev/sdb2 
                                                                               
          11 inodes used (0.00%, out of 1310720)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
      126322 blocks used (2.41%, out of 5242880)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files

```

...and for sdb4:

```

root@sysresccd /root % e2fsck -C0 -p -f -v /dev/sdb4
                                                                               
          11 inodes used (0.00%, out of 3448832)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
      295352 blocks used (2.14%, out of 13769745)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files

```

...doesn't seem to be any issues flagged here! Can't explain it.

If I attempt a mkswap however:

```

root@sysresccd /root % mkswap /dev/sdb3
mkswap: /dev/sdb3: warning: wiping old swap signature.
Setting up swapspace version 1, size = 2 GiB (2147479552 bytes)
no label, UUID=39b8f8df-31ba-44a9-a437-8a3e3a79637d
**[COLOR="#FF0000"]mkswap: write failed: Remote I/O error[/COLOR]**

```

:( :( :(

Running parted also produces an error:

```

root@sysresccd /root % parted -l                    

Warning: Error fsyncing/closing /dev/sdb1: Remote I/O error
Retry/Ignore?

```

...which ultimately after many (i)gnores - (r)etry fails in perpetuity!

```

Warning: Error fsyncing/closing /dev/sdb1: Remote I/O error
Retry/Ignore? i                                                           
Warning: Error fsyncing/closing /dev/sdb2: Remote I/O error
Retry/Ignore? i                                                           
Warning: Error fsyncing/closing /dev/sdb3: Remote I/O error
Retry/Ignore? i                                                           
Warning: Error fsyncing/closing /dev/sdb4: Remote I/O error
Retry/Ignore? i                                                           
Warning: Error fsyncing/closing /dev/sdb: Remote I/O error
Retry/Ignore? i                                                           
Model: TOSHIBA MK8025GAS (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                 Flags
 1      1049kB  3146kB  2097kB                  BIOS boot partition  bios_grub
 2      3146kB  21.5GB  21.5GB  ext4            Linux x86 root (/)
 3      21.5GB  23.6GB  2147MB  linux-swap(v1)  Linux swap
 4      23.6GB  80.0GB  56.4GB  ext4            Linux /home

```

Should I just resign to the (potential) fact that this drive will work flawlessly in Windows, but won't in Linux?

Thanks for your continues support. You're giving me hope. ;)

---

### Post by sudodus on 2017-08-15
> **fiddybux said:**
> Thanks for your input into this. 

Everything helps!

However, I've tried a short wipe many times now and it results in the same I/O error every time. :mad:

Currently part way through a full wipe with mkusb, but I'm expecting the same I/O error right at the end to be honest.

What happened after the 'full wipe with mkusb'?

If it failed, there are **bad sectors** on the drive, or **maybe it is continuously failing** (more and more sectors are turning bad). I am not sure, I hope things are better, but we cannot exclude this scenario. Have a second look at this link:

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

It is also possible, that there are problems with the RAM, that Ubuntu but not Windows is using some RAM location, that is failing and creating confusion. You can check the RAM with **memtest** from the boot menu (in BIOS mode).

It could even be a **problem with power supply** of the USB drive, that there is not quite enough electric power (tension and current) for correct operation. Is there a separate connection to the power grid from the external case of the problematic drive?

---

### Post by fiddybux on 2017-08-15
> **sudodus said:**
> What happened after the 'full wipe with mkusb'?

If it failed, there are **bad sectors** on the drive, or **maybe it is continuously failing** (more and more sectors are turning bad). I am not sure, I hope things are better, but we cannot exclude this scenario. Have a second look at this link:

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

It is also possible, that there are problems with the RAM, that Ubuntu but not Windows is using some RAM location, that is failing and creating confusion. You can check the RAM with **memtest** from the boot menu (in BIOS mode).

It could even be a **problem with power supply** of the USB drive, that there is not quite enough electric power (tension and current) for correct operation. Is there a separate connection to the power grid from the external case of the problematic drive?

Thanks for the suggestions.

I'm ruling out RAM because I have multiple PC's and the Lacie drive responds the same on both when disk management / formatting is attempted in Linux. One machine is a Lenovo T500 (quite old) and the other is an Asus G750 (quite modern). I've run live usb/CD's from both of these machines, and the Lacie drive behaves the same on both. 

After the full wipe in mkusb it failed with the same Remote I/O error.

I'm also ruling out power supply, because the drive works fine in Windows on either the T500 or G750 machines. I've just run a full surface scan in Windows too, and not a single block was flagged. This of course doesn't mean 100% that there aren't any; just that the software didn't detect any.

Thanks for the link; I'll take a look.

---

### Post by fiddybux on 2017-08-15
I'm halting my efforts now...this has beaten me.

Since the drive works fine in Windows, I'm going to virtualise in VirtualBox and use the whole 80GB Lacie drive for the VM disk image.

It's not quite a lean as I'd hoped, but if I use a lightweight OS it shouldn't make much of a difference on my most powerful machine.

Cheerio!

---

### Post by sudodus on 2017-08-15
> **fiddybux said:**
> Thanks for the suggestions.

I'm ruling out RAM because I have multiple PC's and the Lacie drive responds the same on both when disk management / formatting is attempted in Linux. One machine is a Lenovo T500 (quite old) and the other is an Asus G750 (quite modern). I've run live usb/CD's from both of these machines, and the Lacie drive behaves the same on both. 

After the full wipe in mkusb it failed with the same Remote I/O error.

I'm also ruling out power supply, because the drive works fine in Windows on either the T500 or G750 machines. I've just run a full surface scan in Windows too, and not a single block was flagged. This of course doesn't mean 100% that there aren't any; just that the software didn't detect any.

Thanks for the link; I'll take a look.

Maybe the electronics in the external casing is not compatible with the available linux drivers of Ubuntu. The hard disk drive might work with Ubuntu in another external casing. I have tried several external casings and 'USB to IDE and SATA cables' alias adapters. Most of them (but not all) work well with Ubuntu and other linux distros.

> **fiddybux said:**
> I'm halting my efforts now...this has beaten me.

Since the drive works fine in Windows, I'm going to virtualise in VirtualBox and use the whole 80GB Lacie drive for the VM disk image.

It's not quite a lean as I'd hoped, but if I use a lightweight OS it shouldn't make much of a difference on my most powerful machine.

Cheerio!

I can understand that you give up using this drive directly for Ubuntu. I think **Lubuntu** will work well for you in VirtualBox. Good luck :-)

---

### Post by fiddybux on 2017-08-15
> **sudodus said:**
> Maybe the electronics in the external casing is not compatible with the available linux drivers of Ubuntu. The hard disk drive might work with Ubuntu in another external casing. I have tried several external casings and 'USB to IDE and SATA cables' alias adapters. Most of them (but not all) work well with Ubuntu and other linux distros.

I can understand that you give up using this drive directly for Ubuntu. I think **Lubuntu** will work well for you in VirtualBox. Good luck :-)

Quite possibly. I've had it open in the past and it is not SATA, so it's probably PATA and looks quite old. It might just be a weird hardware incompatibility. The drive though, health wise, checks out everywhere on Win.

I'm not a huge fan of LXDE, which is why I'm going for Xubuntu instead.

Thanks again. No idea how to mark this thread as closed, because it's not solved. Haha.

---

