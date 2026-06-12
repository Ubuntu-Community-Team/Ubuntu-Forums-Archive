---
title: "Is it possible for me to..."
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by theonlykman on 2007-04-25
... copy the windows partition on my laptop's harddrive to an external USB harddrive using DriveImage7 and be able to boot to it with grub? I rarely use windows and I want it (20 GB) off of my laptop (60 GB) to make room for the stuff thats on my usb harddrive (movies, music and torrents-in-progress that are more useful to me when they are portable than on the external harddrive). But  I still need windows for neccessary (albeit very few) programs. 

I dont think Ill have a problem copying the files on the partition...as we speak Im using partition magic to create an ntfs partition on the usb harddrive. The quesiton is will I be able to boot it?
Thanks

---

### Post by voided3 on 2007-04-25
Hello, depending on what type of applications they are, installing VMware server may be a good idea. It allows you to create a Windows virtual machine and run it inside Ubuntu at near native speed, plus you can save the virtual machine anywhere. I tried it out on my desktop (1.4ghz Athlon XP, 768mb RAM) and it was exactly the same speed. The only place where you lose out is in 3D acceleration; i.e., most games might have some trouble running on it, though I did get Need for Speed II SE to work :-) If you need it for office or image editing style stuff, it should fill the bill. I believe that there also is a way to convert an existing windows install into a virtual machine, but I think a fresh OS install is always the best. As per your idea of grub loading from an external drive, I personally have never tried it, but perhaps someone else has, however I am under the impression that it is more intended for internal drives and partitions (i.e. the list might not autodetect new bootable volumes, especially via USB). Good luck!

---

### Post by theonlykman on 2007-04-25
yeah, Ive thought abotu VMware. Ive even used wine to run explorer...but theres just something about needing to keep the OS intact. Call it an irrational feeling or superstition, but Id rather like to have xp around somewhere (but off my laptop) even though its not at all my primary system. And would VMware run Solidworks?

---

### Post by theonlykman on 2007-04-26
SUCCESS! ...kinda. so after copying the windows partition onto my usb harddrive, and after some tinkering with menu.lst I got it to boot ( I think) to the external harddrive. I know this (I think) because I can boot to hd0,0 (original windoze partition) and also hd1,1 (new - for a while I had it set to hd1,0 and it wasnt working but I realized I have a FAT partition on the drive too so I changed it to hd1,1 and it booted!) However, even though booting through hd1,1 works...out of curiosity, while in windows, when I removed the usb drive windows still ran. Now, when one removes a harddrive that the current operating system is on, one expects it to not work.
So Im guessing that the only way to see whether or not it really works is to remove the original partition in which case, if it doesnt work Im screwed because theres no (easy if any) way for me to recover windows from the usb drive. Is there any other way that I can actually tell if I can run windows off of my external harddrive?..so far I know it boots fine (I think).

---

### Post by theonlykman on 2007-04-27
ok, so Ive figured out that I can set my bios config to set the boot priority of the usb hd higher than the laptop's hd I. It didnt work, but only because it said that it was missing the system32/hal.dll file, which leads me to believe that DriveImage didnt do exactly what I wanted it to do. I scratched that idea.
Also, Ive been doing some research and one problem (sort of the main obstacle for this type of thing I suppose) with doing what Im attempting to do is that when windows boots it refreshes the usb layer...and when you're booting from a usb device thats a bad thing :(. But I at least wanna get that far so I know that I tried it and it didn't work. 

Anyway, to copy the partition I'm now using the method presented here:
[http://www.sysdesign.ca/guides/partitions.html](http://www.sysdesign.ca/guides/partitions.html)

I've already set up proper partitions using cfdisk:
> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            5101        7297    17647402+   f  W95 Ext'd (LBA)
/dev/sda3            2551        3825    10241437+  83  Linux
/dev/sda4            3826        5100    10241437+  83  Linux
/dev/sda5            5101        5355     2048256   82  Linux swap / Solaris
/dev/sda6            5356        7297    15599083+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            5221       14946    78124063+   c  W95 FAT32 (LBA)
/dev/sdb2   *           1        2550    20482843+   7  HPFS/NTFS

Partition table entries are not in disk order


I have two questions now though. What do I do for an MBR for sdb. Obviously, since I dont have the OS setup that I do on sda, I shouldnt just copy the MBR, right? Or does it not matter since only windows uses the MBR and linux (ubuntu and fedora on my system) use GRUB and chainloader?
Also, because my goal is to minimize as much as possible the amount of space that windows takes up on sda, is there at least a way to just cut it down enough to where I can boot into windows from sda, but run it with program files and such on the external hd?
Thanks

Edit:
I believe this means that dd did its job correctly:
> khalid@khalid-laptop:~$ sudo dd if=/dev/sda1 of=/dev/sdb2
40965687+0 records in
40965687+0 records out
20974431744 bytes (21 GB) copied, 841.076 seconds, 24.9 MB/s
khalid@khalid-laptop:~$ 


---

### Post by theonlykman on 2007-04-27
How can I go about replacing the windows bootloader (since I dont have it anymore) without bootdisks and fixmbr? Couldnt I just find a file with the first 446 bytes of stock mbr somewhere and put it onto the partion wiht dd if=(file) of=/dev/sdb? Does anyone know if such a file exists or where I could get it from. (without bootdisks - since I dont have a floppy drive)

---

### Post by mdurham on 2007-04-27
As far as I remember (it was a while ago) Windows 2K has it's install partition C: D: etc hard coded into something. When I tried moving it from C: to D: it didn't work unless the original was still on C:. When I removed Windows from C: it didn't work and gave me an error message after initial boot about C:\somefile missing. It almost worked, but not quite.
Good luck.

---

