---
title: "Gparted and Installer not seeing my 128 GB SSD Drive with Windows"
date: 2016-01-13
forum: Hardware
---

### Post by markackerman8@gmail.com on 2016-01-13
So from Ubuntu's perspective and sadly grub my SSD drive doesn't exist.

It is a brand new Asus G752V Gaming Laptop Lates of everything that I bought for my twin, and the dual booting problem is areal problem.

I am quite experienced in Ubuntu, but am out of my league here.  Any troubleshooting would be greatly appreciated.  Google is leaving me with no answers.

I installed with the liveCD and in no way was it visible from that either.  It seems I am forced to use EFI Mode, so both are installed in that manor.  Luckily, I guess at least Ubuntu-Gnome boots up nicely.

Please help my brother and me,

Cheers, Mark

---

### Post by ajgreeny on 2016-01-13
[COLOR="#FF0000"]Boot-Repair[/COLOR] in my signature below may help you with this problem.

Run the boot-info script that is offered and do not accept the default repair at this time.  Post back here the pastebin link that you are given and somebody should be able to help you.

---

### Post by markackerman8@gmail.com on 2016-01-13
Thanks for the quick response AJ,

and here is the boot-repair response,

[http://paste.ubuntu.com/14488517/](http://paste.ubuntu.com/14488517/)

I looked through it quickly hoping to see any reference to the SSD drive, sadly none. 

It sees the D: drive in the 1 TB Disk, (refered to always as /dev/sda).  As mentioned the C: drive is on the SSD 128GB (invisible to Ubuntu).

I hope this helps.

Cheers, Mark

---

### Post by ajgreeny on 2016-01-13
I'm a bit lost here; does the machine have Windows on it?

There is a warning in the report you link to of an unsafe ntfs partition sda1, suggesting you have Windows which needs to be shutdown properly, but I don't think you do have Windows from what I see elsewhere in the report.
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
What does ```
sudo parted -l
``` show us when run from the ubuntu terminal?
Does your UEFI/BIOS detect the disk?

---

### Post by markackerman8@gmail.com on 2016-01-13
OK AJ,

Thanks for your time again ... in a nutshell ... parted -l only shows /dev/sda (the 1 TB drive ), This computer is brand new and came with Windows 10 installed on the 128 GB SSD drive (of course windows called it C:), the Windows partition we are seeing on /dev/sda1 is the pre-installed Windows 10 D: drive which was the full 1 TB until I shrank it to 213 GB to install Ubuntu-Gnome.  

w.r.t. "Does your UEFI/BIOS detect the disk? ",I can't check it remotely (I am 3,000 miles away in Vancouver and my Bro and the computer are in Toronto (Canada)).  I ASSUME it does see it and even suspect he can even choose it in Boot Options (F9 in most computers), and intend to ask him when he gets home from his Vet clinic.  I believe it MUST see it, as it was of course fully functional originally and after I down-sized the 1 TB drive.

So as thje original post says ... it, the SSD Drive is still invisible to Ubuntu, Gparted, sudo parted -l, Ubuntu Installer, boot-repair, grub-update and refind as well.

Hence the dilemma

Cheers, Mark


$ sudo parted -l
Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  213GB   213GB   ntfs            Basic data partition  msftdata
 2      213GB   213GB   400MB   fat32                                 boot, esp
 5      213GB   231GB   17.8GB  ext4
 3      231GB   984GB   753GB   ext4
 4      984GB   1000GB  16.0GB  linux-swap(v1)

---

### Post by markackerman8@gmail.com on 2016-01-14
Ok read on if you dare, ...

After a number of hours and many restarts in Ubuntu while not seeing an option to boot into windows and all the problems from above .... 

I decided to to get into Boot Options using ESC to the bios ... "Boot Options" (NOT BIOS itself, to be clear), which had 2 options 1/ with Ubuntu. and 2/ with WIndows.  YAHOO WRONG!!!!!!!!!!!!!!!!!!!!!!

SO choosing Windows indeed popped us into Windows 10 installed on the SSD drive, but when we restarted the laptop NOW it only goes into Windows 

ANDDDD Unbelievably in Start/ ESC/ Boot Options the Ubuntu Option DISAPPEARED !!#%!!!!!!!

Unbelievable!

Please Help

---

### Post by yoshii on 2016-01-14
I would do some more research on dual booting with windows and linux.  And be sure to list which exact version of windows you have and as well the exact type of linux.  And list the model of computer because some of them are known to have tricky BIOSes.  Surely you will get some help because this is a common problem with Windows.  Sorry I can't help any more than that.

---

### Post by yancek on 2016-01-14
I don't use UEFI so have no suggestions other than to read the Ubuntu documentation on the subject at the link below.  Might have been even better to have seen it before installing.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by stunts513 on 2016-01-14
i could take a guess but i don't suggest messing with these options unless you read up on it first. I have a similar issue with a gaming laptop i just got, so far from what i can tell my issue is related to the controller being set to raid instead of ahci in the bios. If you switch this out though without doing some prep work to windows though i believe it breaks the os. Feel free to correct me if i'm wrong. I'm actually about to make a post about mine because while similar i actually have a raid so i can't put it in ahci.

Edit: this also might depend on if its a m.2 ssd or a regular sata ssd. Not positive though.

---

