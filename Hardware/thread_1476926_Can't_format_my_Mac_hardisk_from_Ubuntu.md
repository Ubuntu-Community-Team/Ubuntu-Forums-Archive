---
title: "Can't format my Mac hardisk from Ubuntu"
date: 2010-05-08
forum: Hardware
---

### Post by cboteros on 2010-05-08
Hello everyone,

I have a very interesting issue here... I'll give some background so you understand my problem.

- I have a Macbook 2,1 in which I was running MacOSX, I got this macbook from my previous job and I don't have any MacOSX CD with it.
- One day, the hard disk started to make noises and wasn't working well, so I went to mac and asked them to replace the hard disk so they did
- but... since I don't have a any MacOSX CD, they didn't install any OS to the new hard disk, so I installed Ubuntu and I'm loving it!
- Now... I bought a USB case for the old hard disk and I've been using it as a backup external drive, but since it has the whole MacOS system in it, there is not much free space to use
- Then, I decided that I wanted to format fully the Mac hard disk I'm using with the USB case, but... I'm just not able to do so.

I tried Gparded, fdisk without luck... I'm quite sure this should be possible, unless there is some special "apple protection" in the original hard disk... any clue anyone?

---

### Post by dino99 on 2010-05-08
some info: [http://www.kenstone.net/fcp_homepage/partitioning_tiger.html](http://www.kenstone.net/fcp_homepage/partitioning_tiger.html)

try [http://partedmagic.com/](http://partedmagic.com/)  or [http://www.cgsecurity.org/](http://www.cgsecurity.org/) (testdisk)

---

### Post by aysiu on 2010-05-08
Can you be more specific than "without luck"? What exact procedure did you try and what error message did you get?

---

### Post by cboteros on 2010-05-09
Thank you aysiu, you are right, I should give more details.

I'm trying with System->Administration->Disk Utility

But when I choose to format the drive, it "starts" to do something, and the suddently appears the message:

Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No such device or address

ThenI try again, and I always get that message, so for what I can see, the disk gets unmounted at some point and then this tool doesn't seem to find the drive again.

Similar situation happens with Gparted

---

### Post by aysiu on 2010-05-09
Can you plug the drive in freshly, and then paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste the output back here? ```
dmesg | tail
sudo fdisk -l
dpkg -s hfsplus
dpkg -s hfsprogs
dpkg -s hfsutils
```

---

### Post by cboteros on 2010-05-10
Update: I could set to "zero" part of my hard disk.

With the help of a friend who knows about Linux since long time, I managed to set the hard disk to "zero" by running this command:


```
sudo dd if=/dev/zero of=/dev/sdb bs=1024
```


And now the disk appears as "Unpartitioned" which is good... now I'm trying to create a new partition with another command but I'm getting an error, this is the outopu I get when I run:

```
sudo mkntfs -Q -v -L "CARLOS_POWER" /dev/sdb1
```

```
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
Syncing device. FAILED
```

---

### Post by srs5694 on 2010-05-10
When you zeroed out the disk, you wiped out its partitions, so /dev/sdb1 (which you attempted to use with your mkntfs command) no longer exists. You must first create new partitions on the disk. You can do this with fdisk (for MBR partitions), gdisk (for GPT partitions), or parted or GParted (for MBR or GPT partitions).

Most non-Mac PCs use MBR partitions. Intel-based Macintoshes use GPT partitions. Depending on what computers will use the disk, either system could be more appropriate.

Also, NTFS (probably on MBR) is suitable for use by Windows computers, but if the disk will be used only by Linux, then a Linux-native filesystem (such as ext3fs, ext4fs, ReiserFS, XFS, or JFS) on either MBR or GPT is a better choice. If the disk will be shared between Linux and OS X, I'd go with HFS+ on GPT.

---

### Post by cboteros on 2010-05-10
Thank you srs5694, that I can see clearly, but I'm still having problems just to create the MBR partition with Gparted, It just throws an error message without any explanation.

I would like to try fdisk to create the partition, but I'm sorry to day that I have no clue on how to use this command correctly.

I would like to format this hard disk into a NTFS file system since I'll use it for storage and I might need to connect it to non-linux systems.

Please, any guidance in how to use the fdisk command propertly for this?


If it helps in anything, this is the hard disk I'm trying to format:
Brand: Seagate
Model: ST9120822AS
Size: 120 GB
Web: [http://www.seagate.com/ww/v/index.jsp?vgnextoid=71c88fabfdd83110VgnVCM100000f5ee0a0aRCRD](http://www.seagate.com/ww/v/index.jsp?vgnextoid=71c88fabfdd83110VgnVCM100000f5ee0a0aRCRD)

---

### Post by srs5694 on 2010-05-10
> **cboteros said:**
> Thank you srs5694, that I can see clearly, but I'm still having problems just to create the MBR partition with Gparted, It just throws an error message without any explanation.

The error message *is* the explanation. If you don't understand it, post it. GParted *should* be able to handle a completely blank drive. If it can't, then either you're doing something very wrong (like running it as an ordinary user who lacks permissions) or there's something very wrong with the disk (like a hardware or driver failure).

> I would like to try fdisk to create the partition, but I'm sorry to day that I have no clue on how to use this command correctly.Googling "Linux fdisk use" turns up 1,220,000 hits, including:

[http://www.freeos.com/articles/3935/](http://www.freeos.com/articles/3935/)
[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)
[http://www.dslreports.com/faq/4851](http://www.dslreports.com/faq/4851)

The second of those looks the best, from a very cursory review.

You could also try typing "man fdisk" at a Linux prompt, although man pages are intended for reference by people who are already at least passingly familiar with the program.

> I would like to format this hard disk into a NTFS file system since I'll use it for storage and I might need to connect it to non-linux systems.IMHO, then, you should *not* use NTFS. The problem is that Linux has no good NTFS recovery tools. If the power fails, the system crashes, or you remove the disk from the computer without first unplugging it, the disk will become useless under Linux until you've checked it with the the Windows CHKDSK utility. If your need for Windows compatibility isn't certain, that's a very bad risk to take.

FAT might be an acceptable alternative; it's better supported in Linux and it works as well in Windows. The biggest drawback to FAT is that it tops out at a file size of 4GB, so you won't be able to store big files on it.

If you need big-file support, ext3fs may be a reasonable compromise. This is a Linux-native filesystem, so it'll obviously work well with Linux. It supports files bigger than 4GB. There are Windows ext2/ext3 drivers, so if it becomes necessary to access it from Windows, you'll be able to do so, albeit only after you install appropriate drivers.

---

### Post by cboteros on 2010-05-15
Well, at the end it seems that defenitely the drive has bad sectors in an important place for being able to be formated... so, nothing to do (beside trowing it out of the window, or use it as a paper holder). But thank you everyone for the tips... now... how can I close this thread?

---

