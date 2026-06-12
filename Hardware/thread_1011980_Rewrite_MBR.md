---
title: "Rewrite MBR?"
date: 2008-12-15
forum: Hardware
---

### Post by AndyWooYay on 2008-12-15
I had a 100GB internal drive in my laptop with Windows, which I wanted to replace with a 320GB drive. So I used HDClone Free to create an image of the drive and store it on an external USB drive, and then I copied the image back on to the 320GB drive. 

The only problem is that it copied the MBR too, which tells everything I've tried (except for Ubuntu) that the drive is 100GB. 
Windows ran OK, but I couldn't create any new partitions. I ran gparted and created another partition in the free space area, but now Windows won't boot.

I've tried running fixmbr in the recovery console, but that doesn't work.

fdisk -l shows this:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 cylinders/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1f8e1f8

    Device Boot   Start       End     Blocks   Id
/dev/sda1             1        11      88326   de Dell Utility
/dev/sda2   *        12     11585   92968155    7 HPFS/NTFS
/dev/sda3         11586     11977    3148740   db CP/M / CTOS / ...
/dev/sda4         11978     38913  216363420   17 Hidden HPFS/NTFS

``` 
Any suggestions?

---

### Post by caljohnsmith on 2008-12-15
When you say running fixmbr doesn't work, what exactly happens on start up after doing that? Also what is on partition sda3 and sda4? Neither have a linux file system for Ubuntu. What is your ultimate goal? Are you trying to get a dual boot with Ubuntu, or do you want Windows only on that drive? Also, do you want to resize the Windows partition, or do you want to create maybe a data partition to fill the rest of the drive? Please be as specific as possible about what you are ultimately trying to accomplish.

---

### Post by AndyWooYay on 2008-12-16
> **caljohnsmith said:**
> When you say running fixmbr doesn't work, what exactly happens on start up after doing that?
Windows still won't boot. And by that I mean I see the Windows logo for a few seconds, then I get a blue screen and the laptop reboots itself. 
Edit: Also, if I try running the recovery console, DISKPART sees the drive as full with one 100GB RAW partition, rather than the three partitions totalling 100GB on a 320GB drive.

> Also what is on partition sda3 and sda4? Neither have a linux file system for Ubuntu.
sda3 was on the original drive, I think it's something to do with Dell. I want to move that partition to the end of the drive, resize sda2 to make a bit more space, and then create new partitions for Ubuntu.

Hope that's enough info :)

---

### Post by caljohnsmith on 2008-12-16
In your first post you mentioned:
[QUOTE=AndyWooYay]Windows ran OK, but I couldn't create any new partitions. I ran gparted and created another partition in the free space area, but now Windows won't boot.[/QUOTE]
So when you ran gparted, exactly what partition changes did you make? Did you resize the sda2 Windows partition? Did you change the sda1 partition at all? As long as you didn't move the beginning point of sda2, that's the important point in order to avoid problems. In other words, if you want to resize Windows, be sure to do it from the end of its partition but not the beginning, or you for sure won't be able to boot Windows after that without going through quite a bit of trouble to fix Windows. Of course your Windows is currently broken right now, but you wouldn't want to make things more difficult to fix.

Also, you didn't mention, but what is sda4 for? Is that one of the partitions you tried to create? As long as you want to resize sda2, I would do that first, then create your Ubuntu partitions, and then try to fix Windows afterwards. In other words, I don't think it is worth trying to fix Windows first when you are planning on shrinking its partition anyway; I think it would be better to make your partition changes and then try to fix Windows.

---

### Post by tariquepark on 2008-12-16
hi
i agree with caljohnsmith on the partitioning front. change what needs to be changed, make the ubuntu partitions then fix windows. just be sure not to change the windows partition starting point - THIS IS CRITICAL if youdont want to lose you windows install.
I hope you backed up all your important data before you started?

there is a program i have used quite a few times called mbrwork
it runs from a bootable DOS floppy or usb
it will rewrite standard code restore from backup etc and hasnt failed me yet :) (fingers crossed!!)
grub should take care of things from there

---

