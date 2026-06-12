---
title: "NTFS: files in folder disappeared but still using space"
date: 2012-11-03
forum: Hardware
---

### Post by stinovlas on 2012-11-03
Hi guys, my friend has got a problem with his NTFS partition. He was using Ubuntu and he disconnected power adapter by mistake (it is a notebook but its battery doesnt work anymore) while downloading a movie or something. When he booted again, the whole folder was wiped out. His alternate OS is XP but nothing shows up using windows, either. 

I found [this thread]("http://ubuntuforums.org/showthread.php?t=1845982") but it 1) is not exactly my case and 2) the partition spoke about in the thread is FAT. 

Is there any possibility for me to restore his data? everything else on that partition is still visible, just the one folder is wiped. 

Thanks for any help ;)

---

### Post by imachavel on 2012-11-03
I've got 3 answers for you so I'll give you each one in the most likely order of what I assume will be most beneficial to you

1) your data is wiped out for the windows partition, boot up to Ubuntu partition and look for the file system tree, not the folder that says "file system" but basically "files" where you usually go to get to home. Now look for a folder that says "something or other gb file system." That should be your other file system partition, if you can copy and paste all of those files to Ubuntu. If you don't see it pull your hard drive out and connect it to another computer via a usb to sata transfer device(assuming your hdd is sata) then copy and paste all your files. Then put the drive back in, reformat a new partition, and re install windows on that partition, then transfer all your files back over to windows.

2) maybe it's not that serious. Maybe windows just disappeared from grub. So put your ubuntu disk in and boot to it and look for an option says 'repair boot.' If you don't see it download boot-repair-disk from the internet as an .iso, burn the image to a disk, then boot to the disk, and select 'repair boot'. This should fix any grub or mbr issues with either OS file system.

3) If this doesn't work assuming you can get to Ubuntu partition go to activities and search for boot-repair. It's the same program, and create a boot info summary once opening it. Upload the boot info summary text file and maybe we can figure out if windows is still there. You can get this boot info summary by booting to the boot-repair-disk also but it will most likely give you the grub script of the ubuntu live cd and not of the internal hard drive

---

### Post by stinovlas on 2012-11-03
are you kidding me?

I said the data is not visible from neither ubuntu and windows.

That said, windows did not disappear from the grub and even if it did, it would be very primitive thing to solve.

I am pretty sure windows is still there. and I am pretty sure data is in there somewhere, only it is invisible. DATA partition contains 98 GB of files but there is only 197GB free on 440GB partition.

sda1 - windows
sda2 - ubuntu
sda3 - data
sda4 - swap

all of these partitions are accessable and fully fuctionable except sda3. there is nothing in sda3/video now and even if I copy any file in there it will immediately disappear.


nothing is wrong with grub, booting or windows.

omfg.

---

