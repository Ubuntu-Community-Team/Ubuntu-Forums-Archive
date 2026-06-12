---
title: "Partition Mess"
date: 2015-06-28
forum: Hardware
---

### Post by SepLite on 2015-06-28
Hello Ubuntu Forums, 
So ever since I installed Ubuntu, I've never paid much attention to my partition scheme(?, still new to this don't know what it's called), and now I've run out of space on my Ubuntu partition and run into a bit of a dead end. I want to expand my Ubuntu drive, however that is blocked by the grub partition(of ironically only 1 MB), which is for some reason unmovable(I don't want to risk bricking my computer anyways). I already shrank my windows partition by a bit, so now I just have a bunch of unallocated space around it. Is there anything I could do to resolve this issue? 

[ATTACH=CONFIG]262905[/ATTACH]
Thanks,
SepLite

---

### Post by oldfred on 2015-06-28
Are you booting with UEFI or BIOS. It looks like you have an ESP - efi system partition. And that Windows boots in UEFI.
The bios_grub partition is only required if booting Ubuntu in BIOS mode on a gpt partitioned drive.

You cannot edit or modify mounted partitions. So you have to use your Ubuntu live installed DVD or flash drive to edit your partitions.

Moving partitions particularly moving left can cause all sorts of issues. Best to have good backups as any interruption of a partition move corrupts all the data. 

Also do not move Windows left with gparted. If Window own disk tools let you, then maybe you can, not sure. But it will require chkdsk after any change. So best to have your Windows repair flash drive handy, just in case.

Your drive is starting to get full. Windows NTFS partitions really like 30% free space inside the partition to run well. At 10% free it gets real slow. Linux also needs some room, perhap not quite as much as Windows. Linux ext4 partitions do hide 5%, just to try to prevent you from crashing system if too full.

I prefer to use 25GB for / (root) and actually use about half of that. But I have all data in data partition. I used to also have a separate NTFS data partition when I still booted Windows XP, but now have no Windows. I kept my XP partition smaller and had a d: drive for data. That way I was not writing data into the Windows system partition which can overtime cause issues.

---

### Post by weatherman2 on 2015-06-28
Try booting from the live USB Ubuntu again instead of trying to do this from your booted installation of Ubuntu.  Then you may be able to move that tiny boot partition.

However, FYI, growing that ext4 partition in your scheme means moving it FORWARD, which may be quite time consuming.  (Growing a partition at the end on the other hand is usually quick maybe a few seconds.)

Before doing anything with your partitions - always a tad risky though usually safe - always backup your important data.  If you have some sort of external backup drive, that's probably best.  If you happen to have 500GB of free space on an external drive, even better would be using Clonezilla to make a full backup of your 500GB drive (as an image) so you'd have the ultimate "undo" in case something gets messed up - then you could completely restore the whole hard drive to the way it is now.

---

### Post by NoWayWin8 on 2015-06-28
I would move the 1MB /dev/sda5 partition back so it is adjacent to the windows partition (instead of separated by 39GB of unallocated space as it currently is). Or maybe delete sda5 since it looks like it doesn't belong there. Once you move or delete sda5, you'll be able to move the Ubuntu partition back and then be able to grow it by another 39 GB.

And you will have to boot from a LiveCD/USB to do anything to the Ubuntu partition.

---

### Post by SepLite on 2015-06-28
Wow thanks for all the quick responses(I wasn't expecting any until a day later)!
When I actually attempted it a while ago, I used a live puppylinux drive, however I was lazy when I decided to post this thread and just did it from Ubuntu.

> Are you booting with UEFI or BIOS. It looks like you have an ESP - efi system partition. And that Windows boots in UEFI.
The bios_grub partition is only required if booting Ubuntu in BIOS mode on a gpt partitioned drive.

You cannot edit or modify mounted partitions. So you have to use your  Ubuntu live installed DVD or flash drive to edit your partitions.

Moving partitions particularly moving left can cause all sorts of  issues. Best to have good backups as any interruption of a partition  move corrupts all the data. 

Also do not move Windows left with gparted. If Window own disk tools let  you, then maybe you can, not sure. But it will require chkdsk after any  change. So best to have your Windows repair flash drive handy, just in  case.

Your drive is starting to get full. Windows NTFS partitions really like  30% free space inside the partition to run well. At 10% free it gets  real slow. Linux also needs some room, perhap not quite as much as  Windows. Linux ext4 partitions do hide 5%, just to try to prevent you  from crashing system if too full.

I prefer to use 25GB for / (root) and actually use about half of that.  But I have all data in data partition. I used to also have a separate  NTFS data partition when I still booted Windows XP, but now have no  Windows. I kept my XP partition smaller and had a d: drive for data.  That way I was not writing data into the Windows system partition which  can overtime cause issues.

My Windows is in fact UEFI, although I'm not sure if I should delete bios-grub to be safe. Thanks for the advice, I really hope to only utilize the unallocated space to the left of my Ubuntu partition. There's a lot of junk on my Windows drive(not nearly as much on my Ubuntu drive), so I'll do some cleaning to increase the space on that.


> Try booting from the live USB Ubuntu again instead of trying to do this  from your booted installation of Ubuntu.  Then you may be able to move  that tiny boot partition.

However, FYI, growing that ext4 partition in your scheme means moving it  FORWARD, which may be quite time consuming.  (Growing a partition at  the end on the other hand is usually quick maybe a few seconds.)

Before doing anything with your partitions - always a tad risky though  usually safe - always backup your important data.  If you have some sort  of external backup drive, that's probably best.  If you happen to have  500GB of free space on an external drive, even better would be using  Clonezilla to make a full backup of your 500GB drive (as an image) so  you'd have the ultimate "undo" in case something gets messed up - then  you could completely restore the whole hard drive to the way it is now.


I do have a backup of my most important data(there's not too much of it). 

> 
I would move the 1MB /dev/sda5 partition back so it is adjacent to the  windows partition (instead of separated by 39GB of unallocated space as  it currently is). Or maybe delete sda5 since it looks like it doesn't  belong there. Once you move or delete sda5, you'll be able to move the  Ubuntu partition back and then be able to grow it by another 39 GB.

And you will have to boot from a LiveCD/USB to do anything to the Ubuntu partition.

Okay, this is what I tried to do originally, however, I run into the picture shown below, with a warning message and the move and resize options are greyed out.
[ATTACH=CONFIG]262909[/ATTACH]

Thanks again!
SepLite

---

### Post by weatherman2 on 2015-06-28
I hadn't encountered a bios_grub partition before, but according to this, it should be there only if booting from BIOS (not EFI):

[http://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition](http://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition)

So I agree with NoWayWin8: delete that partition.  Can you delete it despite the warning?  If you are booting Windows EFI you should be booting Ubuntu that way too, right?  I don't think you can boot mixed EFI or legacy/BIOS can you without changing modes.  Perhaps it is there because you originally installed Ubuntu in non-EFI mode?

I think at worst, you could re-create that bios_grub partition later then run boot repair from a Ubuntu live boot, assuming you have one.  Deleting it sounds pretty safe.

---

### Post by oldfred on 2015-06-28
You should be able to delete the bios_grub. Gparted is giving the warning as it is not formatted, which it should not be. The Microsoft reserved is also unformatted, so same warning, but it is required by Windows, so do not delete it.

But the warning on your main NTFS partition may be because you left fast start up on in Windows. That is hibernation to make users think Windows is really faster when they just have enabled hibernation all the time. But that hibernation can cause all sorts of issues if dual booting, even if dual booting another Windows.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by SepLite on 2015-06-29
Thanks everyone!
I deleted the bios_grub partition and expanded my Ubuntu drive successfully, so I went ahead and marked this thread as solved.

However, I have already disabled fast startup on Windows a while ago, and when I looked closely GParted stated:

 "Unable to read the contents of this file system!Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g."

[ATTACH=CONFIG]262918[/ATTACH]

Executing sudo apt-get install ntfsprogs returned: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'ntfsprogs' has no installation candidate

```
and ntfs-3g is already installed on my computer.

---

### Post by SepLite on 2015-06-29
Sorry for double-posting.

To be honest, I don't really need to fix the ntfsprogs / ntfs-3g warning because I have tools installed on Windows for changing the Windows partition if I ever need to, and like you guys have said, I probably should not edit the Windows partition using GParted.

Thanks,
SepLite

---

