---
title: "USB died - save me!"
date: 2009-06-02
forum: Hardware
---

### Post by nuclearcandy on 2009-06-02
today I was trying to install the Microsoft 7 RC (which was a tremendous failure) and screwed up my Sony Micro Vault.  I was in the process of reformatting it in command prompt (running vista on my laptop) to NTFS, but the computer rebooted partway through.  Now my laptop recognizes the device but shows that there is no free space (in fact, no space at all) and no format and won't access it.  Right now I'm on my desktop (running Ubuntu 9.04) and am trying to save the formatting.  Ubuntu is giving a "can't mount file" error when i try to mount the drive.  The USB disk was a gift and I'd really like to save it if I can.  Does anybody know how I can change the format back to FAT?  There's no data on the disk that I am worried about saving and I already tried the windows reformat.  Please help me!

---

### Post by cak3 on 2009-06-02
When it is saying it can't mount it, it means that it cannot mount the partition (in this case, this is probably only one on the drive). Since the filesystem is probably corrupted, that understandable. It can probably detect the drive just fine, unless it has sustained physical damage (which is unlikely, unless you dropped it or something like that.) 

Fortunately, assuming its just the filesystem and not the disk itself, its a pretty easy fix. You need to remove the partition on the drive and replace it with a new one. You can do this from the terminal, but its a lot easier to do with gparted. You can install gparted via synaptic or add/remove programs, or just run
```
sudo apt-get install gparted
``` in a terminal.
After that, have your USB HDD plugged in and open up gparted (should be under Administration, called Partition Editor or somthing like that). Ignore the rest of this is you are familiar with gparted already.

This next part is important, as you can accidently format your desktop's HDD (I have done that...). Your desktop's HDD is probably already selected (there is a drop down box that lists the drives). Probably something like /dev/sda. The external, as the most recently added drive, will probably be the last item in the box, so select it but check to make sure it is correct. (ie. disk size is right, probably will complain about the partition being messed up). 

Once you have the right one, delete the partition on it, the create a new primary partition formatted fat32 (or whatever you want) that takes up the space left vacant by the broken one. Then apply it, and if all goes well you should be good. If it still doesn't work, you could try writing a new partition table to the device (there is an option for that in gparted too, somewhere).

---

