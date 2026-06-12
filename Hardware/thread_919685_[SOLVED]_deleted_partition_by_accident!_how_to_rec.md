---
title: "[SOLVED] deleted partition by accident! how to recover it"
date: 2008-09-14
forum: Hardware
---

### Post by newbuntuxx on 2008-09-14
hey guys

this is one of the latest idiotic things that I've done. While trying to install ubuntu on another computer that i have, I forgot that I had my external hard drive plugged to the PC via USB port. So, when I got to the partitioning part of the installation, I noticed an extra partition that shouldn't be there, so, I went a head and deleted it without thinking, and continued with the installation. Nothing was installed or written to that partition during the installation, however, all the data that I had on that partition was gone! 

The external HD was my back up drive. I had giga bytes of family pics and giga bytes of info saved over the period of 5 years. It was an NTFS format or at least i think, because i don't exactly remember. 

Now, I did a few google searches and came across an open source software called TestDisk for data recovery. But before i use it, i just wanted to get some tips from you guys, or if you perhaps have a better software that I can use to recreate the partition and recover the data. 

I hope I posted this in the right forum.

any help is appreciated!

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi newbuntuxx, depending how much you value your informations, you may start keeping an image of your existing (now screwed up disk).

You would need to buy another disk bigger than your backup disk to do so though.

With this image, you could restore your backup drive to the state it's in now if you screw it up even more while trying to restore some files from it.

That would depend on the value of your informations though.

PS: Sorry for your loss btw :(

---

### Post by newbuntuxx on 2008-09-14
Hey Yannick, 

great suggestion, now, I understand there is a partimage to create the image, the problem is, since i deleted the partition, i can not mount it on my ubuntu machine anymore. When I do fdisk -l, it does not list it there.

Any ideas?

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **newbuntuxx said:**
> great suggestion, now, I understand there is a partimage to create the image, the problem is, since i deleted the partition, i can not mount it on my ubuntu machine anymore. When I do fdisk -l, it does not list it there.

Any ideas?

Yep,

To make an image of an existing disk :

- Have space somewhere to store the entire image in one file, if you have a usb disk, you want it formatted as ext3, not fat32, which has a 2G file size limitation.

- Use dd if=/dev/yourdisktoimage of=/media/destination/imagefile.img

Edit: dd must be run as root (so use sudo if you have to)

---

### Post by newbuntuxx on 2008-09-14
but how can i mount it so i can image it?

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **newbuntuxx said:**
> but how can i mount it so i can image it?

It should NOT be mounted.

Dd will copy an exact image of your backup disk A, exactly as it is now, into a file on another disk B.

In case this is not clear, this will not recover any of your files. It's just so that if, when trying to recover your files, you use a tool that modify your disk being recovered A and fail at it, you can restore A to the state it's in now from the image dd has made on B.

BTW, when you'll be looking for tools to recover your files, you may take a look at photorec, in package testdisk, which I have never used but I hear it's good, and gpart, which I have (unsuccessfully) used.

To use photorec (which you should try first), you will need another disk where photorec will copy recovered files (I think).

Gpart will directly modify your disk A with a likely partition table. You want to try those kind of tools last.

There are also some tools available on windows. In fact, there may be more and better tools available to recover your data for windows.

Good luck :)

---

### Post by Oldsoldier2003 on 2008-09-14
Once you have made a copy of your disk you can try using a utility such as testdisk to recover what you can.

---

### Post by IntuitiveNipple on 2008-09-14
There are some terms you need to understand that might help you in recovering the data.

**Partition**

A partition is a range of contiguous sectors on a disk, from <start> to <end>, e.g. 63 to 23450693.

**Partition Table**

The partition table is a group of four sixteen-byte entries in the first sector of a disk (the MBR Master Boot Record). Each group of sixteen bytes contains the details of one partition. Additional secondary *extended* partition tables can be created each of which contains four entries, but is stored in the first of the partition's sectors, not the first sector of the disk.

**File System**

Inside each partition data is stored using a file-system. The organisation of the data is file-system dependent. For example: ext3, reisferfs, NTFS, FAT32, swap.

**Deleting a Partition**

When using partitioning tools, deleting a partition usually consists of simply zero-ing the sixteen bytes in the partition table that represent the partition itself.

Unless you take additional measures, or the tool you use is very thorough, nothing is written to the partition sectors themselves.

The implication of this is that the partition itself is untouched and the file-system is still there, but the pointer to it (the partition table entry) is gone.

**Recovery**

In simple cases where a disk was originally configured with one partition that uses the entire disk, the partition table entry can be recreated using fdisk, cfdisk, or similar command-line tool using the default start and end sector numbers, and setting the partition type to match the file-system (e.g. type = 0x83 for Linux partitions).

If you can show us the output of fdisk related to the disk with the deleted partition we can probably confirm that recreating the partition table entry this way will work.

The nice thing about editing the partition table is that it only affects the first sector on the disk, not the data in the partitions themselves.

Firstly, can you confirm that the disk containing the partition has/had only one partition that used the entire disk space?

Second, identify the device name of the disk in question (e.g. /dev/sdc), and then show us the output of:
```

DEV=sdc
fdisk -ul /dev/${DEV}

```
set DEV to the device name the disk is recognised as (e.g. sdc).

---

### Post by newbuntuxx on 2008-09-14
hey guys..thanks for all the replies

i just went out and bought a 500 gig external hd to use for imaging the lost hd. 

so, I have everything hooked up. here is the output of: sudo fdisk -l:

```
ali@ali-desktop:~$ sudo fdisk -l
[sudo] password for ali: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c6c3c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3047    24474996   83  Linux
/dev/sda2            3048       10949    63472815   83  Linux
/dev/sda3           10950       11435     3903795   82  Linux swap / Solaris
/dev/sda4           11436       30401   152344395   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe94026ee

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3556610

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    b  W95 FAT32

```


this is the lost hd:

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe94026ee

   Device Boot      Start         End      Blocks   Id  System

```

here is the output of: fdisk -ul /dev/${sdb}:

```
ali@ali-desktop:~$ fdisk -ul /dev/${sdb}
last_lba(): I don't know how to handle files with mode 40755

```

now, the other problem is with partimage. When i try to image the lost hd to the new hd, i cant, because the lost hd is not listed. here is a screen shot:

it asks me to select the drive to image, but its not listed there as you can see. any ideas?

thank you very much for the useful info IntuitiveNipple

---

### Post by IntuitiveNipple on 2008-09-14
Right, so /dev/sdb is the drive with the lost partition?

Can you answer my previous question - did that disk have a single partition that used the entire disk? 

Also, what file-system was used by the partition, do your recall (ext3, NTFS, etc.) ?

If so, and assuming the tool you used didn't do something unusual and wipe the partition's sectors, you can have it back and running in 10 seconds simply by recreating the partition-table entry.

---

### Post by newbuntuxx on 2008-09-14
hey,

there was only one partition on it and the file system was NTFS.

thanks

---

### Post by Yannick Le Saint kyncani on 2008-09-14
All right, here are step by step instructions :

- Open a terminal

- Become root with sudo -i

- Remove your screwed up disk A, you don't want to screw it even more.

- Umount your new big disk B with umount /media/*

- Format it as ext3, as fat32 does not support very big files, and image of disk A will be very big : mke2fs -j /dev/sdc1

- Ubuntu may have automatically mounted your new ext3 partition. If not, unplug disk B, plug it again, and open its icon on the desktop to make sure it's mounted.

- In the terminal again, go to disk B : cd /media/yournewpartitionwhichnameyoullhavetofind.

- Plug in disk A

- Check with fdisk again which /dev/sd? is A and which is B, as it may have changed.

- Make a backup image of disk A using dd, not partimage which won't work in your situation. Assuming disk A is /dev/sdc, that would be : dd if=/dev/sdc of=./screwedupdisk.img

- Umount disk B, unplug it and keep it in a safe location.

- Start investigating tools to recover your files, like photorec and testdisk (linux tools) or windows tools, which may be better in your situation.

---

### Post by IntuitiveNipple on 2008-09-14
> **newbuntuxx said:**
> hey,

there was only one partition on it and the file system was NTFS.

thanks

That's good.

Now, listen and read carefully **before** taking any action :)

If only the partition table was zero-ed by the deletion, as seems likely, then the only thing that changed on the disk was the 16 bytes in the first sector.

Therefore you can fix the problem by writing a correct partition table to the disk.

The entire disk doesn't need backing-up to do this since it isn't going to be touched.

In this case it isn't strictly necessary to back up that sector first  either, since it hasn't got anything useful in it - but we will to preserve the methodology:
```

cd ~
sudo dd if=/dev/sdb of=sdb-mbr.bin bs=512 count=1

```
That has saved the 512 bytes in sector 0 of /dev/sdb to the file "sdb-mbr.bin" in your home directory.

Now recreate the partition table on /dev/sdb, creating one primary partition that spans the entire disk and setting it to type 7 (HPFS/NTFS). Start fdisk:
```

sudo fdisk /dev/sdb

```
Press **p** to display the current partition table. **CONFIRM** it is empty. If it isn't, stop now and report what you see.

Press **n** to create a New partition.
Press **p** to create a "primary partition"
Press **1** for partition number 1
Press **Enter** to accept the default start, cylinder 1
Press **Enter** to accept the default end, which will be the last cylinder of the disk
Press **t** to set the type of a partition. Because there is only the one partition it will skip asking the partition number to set the type
Press **7** to set the type to HPFS/NTFS
Press **p** to display the proposed new partition table.

It will look something like:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         366     2939863+   7  HPFS/NTFS

```
except that the End and Blocks count will be different.

Press **w** to write this partition table to the disk and exit.

To have the new partition table recognised you'll need to disconnect and reconnect the disk so it is read.

When you do that the kernel will try to read the file-system in the partition. If it wasn't written to by the deletion process that started this issue, you should then use the file-system specific tools to check the file-system is valid **before** mounting it.

Check that the disk is still known as /dev/sdb at this point.

If the system auto-mounts the file-system in the partition (a very good sign!) before you get chance to prevent it, unmount it and then run the NTFS fix tool to check the basic structure of the disk:
```

sudo ntfsfix /dev/sdb1

```
You may need to install the package that contains that tool:
```

sudo apt-get install ntfsprogs

```
**Note:** After running ntfsfix it will mark the disk in need of checking by Windows. You should move the disk to a PC with Windows on and use Windows **chkdsk** to do that check. Without that, the Linux file-system drivers will usually insist on mounting the drive as read-only, preventing any writes.

If this method doesn't result in the return of the partition and file-system, you can return the first sector of the disk to how it was (empty) using:
```

cd ~
sudo dd if=sdb-mbr.bin of=/dev/sdb bs=512 count=1

```

**Backing Up the Drive**
The simplest and best way to back it up is to simply copy the entire contents verbatim. This will take a while especially if both drives are external and on the same USB hub:
```

sudo dd if=/dev/sdb of=/dev/sdc

```
That won't make the back-up visible as a file-system in any way but it guarantees the back-up image is exactly the same as the original disk.

After the back-up completes you have the opportunity to edit the image (or the original) to get the file-system recognised again.

---

### Post by newbuntuxx on 2008-09-15
hey guys, thanks for the quick replies...

Yannick, I am currently imaging the drive. basically at  this step:

dd if=/dev/sdc of=./screwedupdisk.img

its taking awfully long, and i thought that the size of the .img file will be 250 gigs, since thats the size of the lost hd, however, the file is now 270 gigs and growing! so, i am not really sure why its larger than 250 gigs! its been imaging for 6 hours now. 

thanks for the steps IntuitiveNipple, i will definitely try them once i am done imaging the drive, and I'll let you know the results.

i just pray that the img file will not exceed 500 gigs!

regards

---

### Post by Yannick Le Saint kyncani on 2008-09-15
> **newbuntuxx said:**
> dd if=/dev/sdc of=./screwedupdisk.img

Well, the imaging should be well finished by now. If not, make sure the disk you want to image is still /dev/sdc and not /dev/sdb or /dev/sdd, as plugging/unplugging devices can and will change their /dev/sd* order.

Make sure you're imaging the right drive, because if you're not, then you will think you have a backup when in fact you don't. So if you're imaging the wrong drive, just delete the image and redo the imaging again.

---

### Post by newbuntuxx on 2008-09-16
hey,,

yea, i was imaging the wrong drive! i was imaging the 500 gigs drive that i just bought! so, i corrected that and now i have a back up copy of the corrupt drive.

now, i followed your instructions intuitivenipple to the dot. 

When I created the partition, the table looked like this:

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe94026ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

the drive was NOT automounted. 

So, I ran: ntfsfix, and this is what i got:

```
root@ali-desktop:/media/disk# ntfsfix /dev/sdb1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```

So, I plugged the drive in a windows machine and I ran chkdsk and this is what I got:

```
The type of the file system is RAW.
CHKDSK is not available for RAW drives.

```

can I try anything else?

thanks

---

### Post by Yannick Le Saint kyncani on 2008-09-16
Hi newbuntuxx,

Now that you have a backup image ( double-check : the image file should be about the same size than your original drive ), you should unplug it and store it in a safe location. If you are unsuccessful at recovering your data and about to commit suicide, this image should ( assuming you did it right ) be enough to restore your current situation.

Now, if I were you :

- If you have enough space on another drive, I would first use photorec. I think photorec should be able to recover most of your files, however, it seems photorec won't be able to retrieve the files/directories structure ( all files will be recovered into a single directory ) and you won't get filenames too ( I may be wrong ). This may not be much, but it's still something.

- There are some tools that may be able to recover the entire partition, that means you should be able to see all your files with the correct filenames and content. If you had only ntfs/fat32 partitions, I think windows-only tools may be better than unix tools at recovering your data. You should carefully read howtos/manuals and don't expect to get a "push here and go drink a coffee to recover everything" button. Testdisk is the best tool available in ubuntu at this I think ( although I did not have much luck with it in the past ).

Both testdisk and photorec are available in package "testdisk". And check out windows-only tools (again).

Good luck :)

---

### Post by IntuitiveNipple on 2008-09-16
> **newbuntuxx said:**
> When I created the partition, the table looked like this:

```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe94026ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

```

the drive was NOT automounted. 

So, I ran: ntfsfix, and this is what i got:

```
root@ali-desktop:/media/disk# ntfsfix /dev/sdb1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```

Okay, that looks as if
[list=1]
[*] the first sector (and possibly more) of the partition was over-written when the partition was deleted, *or*
[*] we've simply got the wrong starting sector.
[/list]
Let's hope for the second situation. If you can save and compress the first few sectors of the disk I can take a look at them and determine if there is an NFTS file-system recoverable.

Here's how to do that. Attach the drive and check what name it has (I'm going to assume /dev/sdb as before):
```

cd ~
sudo dd if=/dev/sdb of=sdb-sectors000-199.bin bs=512 count=200
gzip sdb-sectors000-199.bin

```
You've now got the compressed file "sdb-sectors000-199.bin.gz" in your home directory that you can attach to a reply here.

I've chosen 200 sectors since it covers the first two 'logical' cylinders of the disk, and a bit more. As partitioning tools generally still create partitions on those logical cylinder boundaries, this should allow me to see the MBR and the first sectors of the first partition.

---

### Post by newbuntuxx on 2008-09-16
Good news guys :)

I managed to recover the files, and man am i happy! :)

After creating the partition as intuitive nipple suggested, i used photorec as Yannick said, and I was able to retrieve all the files! and it worked! all my files were retrieved. 

Thanks a lot guys...really...thank you :)

---

### Post by Yannick Le Saint kyncani on 2008-09-16
> **newbuntuxx said:**
> Good news guys :)

I managed to recover the files, and man am i happy! :)

After creating the partition as intuitive nipple suggested, i used photorec as Yannick said, and I was able to retrieve all the files! and it worked! all my files were retrieved. 

Hi newbuntuxx, glad to hear that.

I suggest you start using backups from now on.

You should *at least* keep one month of backup on one usb disk.

You may also have another usb disk dedicated to backup that you don't always keep up-to-date (maybe once a year or every two years) but keep it stored in another location like a trusted one's home.

That's what I do anyway, and a handful of dollars weighs nothing, _nothing_, in comparison of years of personnal data.

---

### Post by newbuntuxx on 2008-09-17
I will definitely keep more than one back-up now. At least two. One will be on my PC table, and one stored away for days like this. 

Boy am I glad I got the files back though. I didn't have the balls to tell my family that their pictures (taken over the period of 4-5 years) were "temporarily" lost! They would literally lynch me!

Thanks again to all those who helped, especially Yannick and intuitive nipple!

---

### Post by bhanu verma on 2008-09-30
HI I am Bhanu Verma 
By mistake i deleted the partition form my hard disk is there any way to get my data back . I am facing problem .

=============================================================
Bhanu Verma
===========================================================
[  Attorney ](" 	  http://attorneys.fastrealestate.net")

---

### Post by jcathey on 2008-10-01
If you have not already reformatted the partition (example:  if you just deleted it) then you can use Acronis Disk Director to recover the deleted partition.  I have used this on client's pcs several times and it has worked everytime.  It works from a bootable cd so you do not have to worry about mounting / unmounting the drive in linux.

Hope this helps,

Jeremy

---

### Post by jcathey on 2008-10-01
Also consider using something like jungle disk (an online backup solution through amazon sc3).  It works natively in windows, mac, and linux.

Hope this helps,

Jeremy

---

### Post by utnoobu on 2009-02-21
> **IntuitiveNipple said:**
> Okay, that looks as if
[list=1]
[*] the first sector (and possibly more) of the partition was over-written when the partition was deleted, *or*
[*] we've simply got the wrong starting sector.
[/list]
Let's hope for the second situation. If you can save and compress the first few sectors of the disk I can take a look at them and determine if there is an NFTS file-system recoverable.

Here's how to do that. Attach the drive and check what name it has (I'm going to assume /dev/sdb as before):
```

cd ~
sudo dd if=/dev/sdb of=sdb-sectors000-199.bin bs=512 count=200
gzip sdb-sectors000-199.bin

```
You've now got the compressed file "sdb-sectors000-199.bin.gz" in your home directory that you can attach to a reply here.

I've chosen 200 sectors since it covers the first two 'logical' cylinders of the disk, and a bit more. As partitioning tools generally still create partitions on those logical cylinder boundaries, this should allow me to see the MBR and the first sectors of the first partition.
Hi,

I'm facing a similar problem and I feel I can use a modification of your solution.

Let me give you details of my problem. I've deleted the partition table on my external hard disk, used clean in DiskPart in Vista. Now I'm trying to recover/recreate the partition table, as I do not have the resources to use data recovery tool to extract data from the drive.

The drive was initially 1 NTFS partition. Then I created a second partition of exactly 4096MiB and it was FAT32. My drive is a 320GiB (298GB) Western Digital of which 260GB was full. Could you please help me out with the commands?

Thanks in advance!

---

### Post by caljohnsmith on 2009-02-21
Utnoobu, one of the best tools for recovering deleted/lost partitions is testdisk. To use testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there if you want.

---

### Post by utnoobu on 2009-02-22
> **caljohnsmith said:**
> Utnoobu, one of the best tools for recovering deleted/lost partitions is testdisk. To use testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing partitions. We can work from there if you want.
Hi caljohnsmith,

Thanks for the solution. I've already spent a couple of days with testdisk, all the way upto Deeper Search. Unfortunately, only the FAT32 partition was shown, and I can afford to lose that! This happened every time, hence my post here! If you think you still need to look at the output, I will run it again and post it here.

---

### Post by marzy on 2011-02-02
Hi,

The laptop I didn't this on doesn't have ubuntu on but I was wondering if you guys could help me.

I did the same as OP but I had os x and win xp partition. I was wiping drives with Parted Magic and had the wrong drive selected. I realised straight away what I had done so I haven't formatted. 

I was looking at disk warrior for the mac
or
Data Rescue 3 for the mac

but if you guys know a better way I can boot up off my live CD or install ubuntu on another computer.

Thanks.

---

