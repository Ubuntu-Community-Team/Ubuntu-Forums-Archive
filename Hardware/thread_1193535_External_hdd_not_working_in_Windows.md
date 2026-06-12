---
title: "External hdd not working in Windows"
date: 2009-06-21
forum: Hardware
---

### Post by tospig on 2009-06-21
Hi,

I've got an external hdd that I can plug into my ubuntu machine fine and use it to backup my files, but when I come to plug it into Windows it doesn't work, even though it says it should plug and play. 
I've had a look around the internet and on here, and there's talk about compatibility issues and other things to that nature, but I couldn't make much sense of it. 

Can anyone explain to me (in simple terms please :) why it doesn't work on Windows, and then how to get it to work?

---

### Post by M3TAL1QU1D on 2009-06-21
Maybe its not formatted NTFS or FAT, a filesystem recognized by windows? Ubuntu uses a different filesystem and it could be possible that your external is in the filesystem ext3. 

I could be wrong. Can someone confirm??

---

### Post by tospig on 2009-06-21
potentially, but that doesn't explain why it should just plug and play in windows in the first place...

---

### Post by mtbsoft on 2009-06-22
Not necessarily.  If the drive is not formatted as a Windows partition it simply won't acknowledge its existence.

You could use the administration tools in windows to look to see if the physical device is visible in the Disk Management utilities - it will show as an unknown format disk.  If so, there are windows drivers available to permit you to access it from there.

---

### Post by lisati on 2009-06-22
The first thing to check, as already suggested, is that the drive is formated in a way that Windows can use. The next thing to check is that you didn't just unplug it while *nix was active: like Windows, it's a good idea to "safely remove hardware" (i.e. unmount the HDD cleanly, in ubuntu terminology)

---

### Post by tospig on 2009-06-22
for the filesystem it says 'msdos' (see attached).

---

### Post by mtbsoft on 2009-06-23
Ok, bit of a long shot but I've seen this before with 'doze.

Have you got another device plugged into the computer which is using the same drive latter the the ext. drive previously used?  Sometimes this can cause issues - the letter gets "stuck" to the device and both cannot use the same, so the first gets the letter and the second doesn't get a new one reassigned.

Easy way to tell is if the Unplug Device Safely thing shows you an un-lettered device which you can remove.  If so, use the disk management tools to change the letter of one of the devices and you should be sorted.

---

### Post by tospig on 2009-06-23
Do you mean the Unplug Device Safely thing on Windows? If so, I don't get that option, the drive is not recognised as anything. I get an error saying an unknown device is plugged into a usb port, and that's it.

---

### Post by solitaire on 2009-06-23
The "MS-DOS" is a "disk label type" 

"MS-DOS" just means that it's a disk which can be used for logical & extended partition layout (you can just ignore that bit!!) But different Operating systems may use different types (like BSD).

It looks like the disk was not unmounted in windows correctly (which happens a lot!) or under linux.

Best thing to do is connect the drive when in linux and do a check of the disk. It will tell you if their are any error stopping the disk from mounting.

Also use the partition editor to check what format the disk is in NTFS , FAT or EXT#

---

### Post by tospig on 2009-06-23
How do I check the disk?

---

### Post by solitaire on 2009-06-23
> **tospig said:**
> How do I check the disk?
Start up "Partition Manager" from System /Administrator
Select the USB drive from the drop down menu (usually marked SDB )
Right click on the partition and select "check"

it should say something like:
Check and repair file system (???) on /dev/sdb1
1 operation pending

Then click the green tick at the top and let it do the check....

---

### Post by tospig on 2009-06-23
I may be being a bit stupid, but I can't find 'partition manager'...

I have since discovered that the filesystem says vfat (FAT32)

---

### Post by paul_be on 2009-06-23
Perhaps you are having driver issues in XP.  Do other usb devices work in XP?

---

### Post by tospig on 2009-06-23
yes, I've had no problems with other usb devices on XP

---

### Post by mtbsoft on 2009-06-23
Have you tried plugging the device into another computer running XP to see how it behaves?

---

### Post by magh-87 on 2009-06-23
If the information is still on your ubuntu side, you could format the hdd into a NTFS or FAT32 format which will allow XP to recognize it. After that, your data should be good to go.

---

