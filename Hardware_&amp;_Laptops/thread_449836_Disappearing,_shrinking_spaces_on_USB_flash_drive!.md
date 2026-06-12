---
title: "Disappearing, shrinking spaces on USB flash drive!!"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by missirismissiris on 2007-05-20
I have gotten a 128MB USB flash drive/MP3 player a few weeks ago, and after a few trials I got it working on Ubuntu.

I noticed last week that the available disk space keeps shrinking every time I delete files and put in new files -- 128MB became 112MB, then 89MB, and now (even when it is supposedly empty) has only 77.2MB.  This is after having erased all files with rm /media/scd1/* and then rm /media/scd1/.Trash-myname/* , rmdir /media/scd1/.Trash-myname .

Looking at the information from ls -alh /media/scd1 there is no file left, but still there is this mysterious disappearing/shrinking spaces of nearly 50MB so far.

I then did cfdisk on it, I could see there was one partition the size of 38.5MB and "unallocated free space" totalling 128MB.  So I deleted the partition, then created one big partition with the now 128MB of unallocated free space.

Opening the /media/scd1 with Nautilus I found it to still have only 77.2MB of free space.

Is there a way to find if there is some mysterious stuff hiding somewhere on the USB flash drive taking up 50MB, or is there a way to clean up the drive entirely?  (I have just connected the same drive to a Windows XP computer -- an error message reads "E:\ drive is not formatted. Would you like to format it?")

:(

---

### Post by merlinus on 2007-05-20
Having just had this experience, it is due to a trash folder on the flash drive that is filling up with deleted files.

Simply empty it, and you will have all of the space available again.

Make sure you have Show Hidden Files selected in Thunar or Nautilus, though, or you will not see the trash folder.

The incredible shrinking flash drive!!!!

;)

-merlin

---

### Post by catdriver on 2007-05-20
> I then did cfdisk on it, I could see there was one partition the size of 38.5MB and "unallocated free space" totalling 128MB. So I deleted the partition, then created one big partition with the now 128MB of unallocated free space. ....
.... (I have just connected the same drive to a Windows XP computer -- an error message reads "E:\ drive is not formatted. Would you like to format it?")
 
I suspect that the 38.5mb was the equivalant of the master boot record for this device, and when you deleted it and resized the partition you effectively removed the formatting info for the device.  You will likely have to reformat it to get it to be recognized under winderz again.  I did tis to an iPod once with similar results.

---

### Post by missirismissiris on 2007-05-22
> **merlinus said:**
> Having just had this experience, it is due to a trash folder on the flash drive that is filling up with deleted files.

Simply empty it, and you will have all of the space available again.

Make sure you have Show Hidden Files selected in Thunar or Nautilus, though, or you will not see the trash folder.


I have already done that in the shell by doing:

# cd /media/scd1
# ls -alh
# rm .Trash-myname/*
# rmdir .Trash-myname

In fact, each time I cleared the UFD through this method I keep losing 20MB or so of free space.  This is mysterious... :(

The device is SigmaTel MSCN audio player -- manufactured by a company called Flair (which I have never heard of).  The device was originally formatted as FAT16 (as I saw in cfdisk), and was reformatted FAT16, so I wonder why WinXP no longer recognizes it...

---

### Post by xander.yz on 2007-05-24
I'm experiencing the same problems with my Logic (4GB) flash player.
Already tried the options of emptying trash, and showing hidden files. The player appears to be empty but nevertheless 1GB is already missing. 

The only way, so far, I was able to solve the problem was to plug the player to my windows-operated computer at work and format the flashdrive. 

Unfortunately gparted "does not see" my mp3 player and I cannot format it using this programme either. 

Anyone else experiences similar problems? Anyone knows how to solve them without condescending to windows?

---

### Post by johntkucz on 2007-06-21
I have a similar problem with the .Trash files on the flash drive.
when I go to remove it though, it says it's a Read-only file system

ubuntu@ubuntu:/media/TRAVEL2GB$ sudo rm .Trash-ubuntu
rm: cannot remove `.Trash-ubuntu': Read-only file system
ubuntu@ubuntu:/media/TRAVEL2GB$ rmdir .Trash-ubuntu
rmdir: .Trash-ubuntu: Read-only file system
ubuntu@ubuntu:/media/TRAVEL2GB$ 


Help!

---

### Post by KrIaXPaTaLa on 2007-11-22
Same problem with a 2 GB flash drive, detected as only 1,2 GB. The drive is completly empty (including trash), and works normaly in windows. Is there a known issue with usb drives?

Im using dapper.

Regards,

KX.

---

### Post by Tweenk on 2007-11-22
I suspect this may be some WTF with free space reporting in FAT16. I would try to fill up the disk with copies of 100MB files to see what is the real capacity of the "shrunk" flash drive. Anyone tried this?
Linux-formatted FAT16 won't appear in Windows, you have to manually change the partiotion type through fdisk (because it usually has type 83 - Linux, where it should have type 06 - FAT16). The commands are:
fdisk /dev/[flashdrive device node]
t
1
06
w

---

### Post by KrIaXPaTaLa on 2007-11-29
After a windows format, followed by a linux format, followed by a lot of stupid actions from my behalf, I now have 2 mount points for my usb drive (using gnome-volume-manager):

/dev/sda on /media/usbdisk - whitch now detects the free space correctly (!!)

/dev/sda1 on /media/usbdisk-1 - witch shows me the last free space detected before all these actions (166 MB) but is read-only, so I cant cant delete the garbage (buntch of no name files) in there nor use this drive period.

I am also not able to umount this usbdisk-1, giving me the 'device is busy' routine. Today, unplugin the usb disk from the port cost me a system crash with reboot :\

I've also changed to fluxbox from gnome now (today, not related to the 2 mount points), but I reckon this doesnt influence the behaviour of gnome apps like gnome-volume-manager, so the crash was due to the simple removal of the drive.

Any ideas about the 2 mount points, at least?

Regards.

PS: But the wrong free space issue was solved with the help of this thread, tnks.

---

