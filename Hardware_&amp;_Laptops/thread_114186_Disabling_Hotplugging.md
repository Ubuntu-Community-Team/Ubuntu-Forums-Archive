---
title: "Disabling Hotplugging"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by aimless on 2006-01-08
Does anyone know  how I can disable hotplugging, at least for my iRiver USB mp3 player??  I'm trying to get it to mount writable. I've given up trying to figure out a way to get hotplugging to do this (Verrrrrrry Frustrating). Just want to mount it manually as I'm pretty sure I can figure out how to get read write access this way.
     From the posts I've seen on these forums, hotplugging USB devices seems to be an issue with Ubuntu. (I never had this problem with mandriva).Although I'm very impressed with Ubuntu in every other way I can't believe no one seems to know a straightforward  fix for this problem.HELP!!!!!

---

### Post by superm1 on 2006-01-08
[QUOTE=aimless]Does anyone know  how I can disable hotplugging, at least for my iRiver USB mp3 player??  I'm trying to get it to mount writable. I've given up trying to figure out a way to get hotplugging to do this (Verrrrrrry Frustrating). Just want to mount it manually as I'm pretty sure I can figure out how to get read write access this way.
     From the posts I've seen on these forums, hotplugging USB devices seems to be an issue with Ubuntu. (I never had this problem with mandriva).Although I'm very impressed with Ubuntu in every other way I can't believe no one seems to know a straightforward  fix for this problem.HELP!!!!![/QUOTE]

I wouldn't flat out disable hotplugging for a quick fix here.  First lets take a few stabs at the exact problem....

Now lets say your logged in as Bob.  When you login, gnome-volume-manager should be spawned under Bob's login name.  Any devices plugged in should be recognized by that instance of gnome-volume-manager & mounted with permissions for Bob to take care of them.  Now if you mount this device under Bob, and then switch to Caroline - then permissions wouldn't allow for her to write to the device.  So does that match your scenario at all?

If not, check and see who is running gnome-volume-manager, if by some fluke it is root - that might be why things are going a bit wacky.

---

### Post by Amon_Re on 2006-01-08
Also check dmesg for messages when you plug it in, when plugged in also see with fdisk if the device is listed, and lastly mount to see if it's mounted, and as what & where.

sudo dmesg
sudo fdisk -l
sudo mount

---

### Post by aimless on 2006-01-08
A quick summary of answers to all your questions
  
           1.) I did not change users

           2.) I am the user running gnome volume manager
  
           3.)  The device is listed in fdisk
     
           4.)  The device is mounted as /dev/sda on /media/usbdisk

           5.) When running  dmesg I get the following  message over and over again

                             FAT: Filesystem panic (dev sda)
                             invalid access to FAT 




 The device works fine in Win XP and other linux distros I've used. Any help would be greatly appreciated.

---

### Post by Amon_Re on 2006-01-08
I've never ran into this FAT: Panic error, but my first guess would be that the fs is somehow corrupted in a way that hinders linux from properly mounting it, while XP might be more tolerant to FS errors.

Check the disk from XP, just to be sure

---

### Post by superm1 on 2006-01-08
[quote=Amon_Re]I've never ran into this FAT: Panic error, but my first guess would be that the fs is somehow corrupted in a way that hinders linux from properly mounting it, while XP might be more tolerant to FS errors.

Check the disk from XP, just to be sure[/quote]

XP's chkdsk should be able to handle this, and if you leave it plugged in when booting, XP should flag it for the scan on boot (if for a change things work in XP).

Most corruption occurs on these usbdisks from just pulling them out without properly ejecting.  Even in windows you should be doing this, it will help the life of the device too.

---

### Post by aimless on 2006-01-08
I'll give that a shot.

---

### Post by aimless on 2006-01-08
Thank You, Thank You, Thank You. I followed your advice and it worked like a charm. In the future I'll have to be more careful about when I unplug my iRiver.
    I'm liking Ubuntu (and these forums) more and more every day.

---

