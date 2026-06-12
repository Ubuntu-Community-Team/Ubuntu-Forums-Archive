---
title: "Slave Hard Drive Not Detected"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by chocomoojuice on 2006-12-08
I am a new Ubuntu user, previously used Windows XP.  On my previous setup, I had two hard disks: a 160gb primary drive consisting of the OS and program files and a 40gb secondary drive for storage of personal files such as music.  Since I am just trying out Ubuntu, I'm using an alternative 10gb primary drive.  So my current hard disk set up is:
10gb primary hard disk
40gb Maxtor slave hard disk

Anyways...during boot up, the 40gb is detected.  When I enter the BIOS, it recognizes the two hard disks as the following:
IDE Primary Master [WDC WD400BB-60DGA0]
IDE Primary Slave [Maxtor 6E040L0]
Where the primary slave is indeed the 40gb Maxtor.

Once I boot up into Ubuntu, and go to Places > Computer, I see no other hard disks other than the 10gb drive, named Filesystem.  The 10gb was completely reformatted during installation, but the secondary has not been formatted since the previous XP installation, and thus contains data important to me.  I am unsure of the partition of the 40gb; NTFS or FAT32, and am unsure as to whether this is important.

Sorry if this question has already been answered.  I made sure to scour the forums before posting.
Thanks in advance,
James

---

### Post by taurus on 2006-12-08
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by chocomoojuice on 2006-12-08
Ok, I've tried following this tutorial, but am continually unable to follow certain parts, and am getting stuck at one step in particular.  So, I'll follow the steps on the site, tell you my process, and where I eventually get stuck:
The first step where it asks me to unmount my windows partitioned hard drive, I am unable to do.  This is because I'm unsure of the mount point of the drive, so I continue onto the next step.

So then, I type "sudo fdisk -l" into the terminal.  The results are as follows:

Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4997    40138371    7  HPFS/NTFS


So, from this, I can see that my 40gb drive is at /dev/hdb1.  I then assume that the mount point must be /media/hdb1, but when I try to unmount this, it fails telling me "umount: /media/hdb1: not found".  I resume trying the steps that follow.

I type "sudo mkdir /windows", and the directory is successfully created.  No trouble in this step

"sudo cp /etc/fstab /etc/fstab_backup" also succeeds.

I then open the fstab file by typing "sudo nano /etc/fstab", which works, however, this is what I read:

proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=95fd2cef-b582-4cca-a413-13cf5610d94c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0dc2803e-d35f-47fd-be0f-357bae7ccc0b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


I make note of the fact that this file is formatted differently on Ubuntu 6.10.  Regardless though, I notice that the 40gb drive /dev/hdb1 is not listed.  Thus, I can't edit it.  This is my predicament.

I read on, even though the next set of steps are made specifically for FAT32 users.  I consider adding lines to fstab like they do for a FAT32, but then realize that this is the format for an older version of Ubuntu.  In the newer version, the UUID is stated, and I don't know the UUID of the 40gb drive.  I'm also not sure as to whether I could use the old format and simply add the line:
"/dev/hdb1 /windows ntfs iocharset=utf8,umask=000 0 0"
(Note:  if you suggest that I add this line, should I put umask=0222 0 0 or umask=000 0 0)

Thanks for your previous response, any help is appreciated!

---

### Post by taurus on 2006-12-08
Personally, I would add this entry to /etc/fstab to mount that Windows partition...

```
gksudo gedit /etc/fstab
```
```
/dev/hdb1   /media/windows   ntfs   iocharset=utf8,umask=0222   0   0
```
Then, create a mount point and mount it...

```
sudo mkdir /media/windows
sudo mount -a
df -h
```

---

### Post by chocomoojuice on 2006-12-08
YAY!!!  Your suggestion worked.  However, I do notice that I cannot cut, create or paste files.  Is this drive read only at this point.  If so, is there a way to make it writable as well?

P.S.
I'm completely new to Linux, so naturally, I have a question that is most likely obvious to you, but not to me.  Anyways...does Linux create and format folders differently than a Windows based system?  In other words, if I were to make changes on this drive, would the same drive then not be compatible on a Windows based system?  Are all these creation of directories making the drive inaccessible on a Windows based system?

Thanks for your continuing help,
James

---

### Post by taurus on 2006-12-09
Yes, right now, you only mount your ntfs as read-only.  If you want to write to it, you need to install ntfs-3g and modify the entry for /dev/hdb1 in /etc/fstab a little bit.  Here's a link for it...

[http://ubuntuforums.org/showthread.php?t=217009/](http://ubuntuforums.org/showthread.php?t=217009/)

---

### Post by chocomoojuice on 2006-12-09
> Warning : ntfs-3g is still in beta. You should not use it on production machines.
If you can, it's always better to prefer ext3 to share file between windows & linux using [http://fs-driver.org/](http://fs-driver.org/)
Considering that's what I read when I enter the page, I think I'll back down on that option and just accept this drive as being read only.  Thanks for the suggestion and all your help though.  This makes my Ubuntu experience way more fun when I can access my tunes :D.

---

