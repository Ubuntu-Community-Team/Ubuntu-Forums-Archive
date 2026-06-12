---
title: "Which driver NTFS driver should I use for moving files from Windows to Ubuntu?"
date: 2009-05-15
forum: Hardware
---

### Post by learningcurb on 2009-05-15
Note: I'm aware there are other threads covering NTFS, but I can't seem to find one that covers the multiple driver choices.

So here's the deal, I finally made the switch to Linux and it's great so far.  However, now I want to move all my data from my windows drives to my ext3 partition so I can reformat the old drives for use with Linux.

I installed disk-manager, a GUI tool for handling disks and I let it auto configure the disk and mount it.  I read at [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) that NTFS-3G should be used.  However when I look at the possible settings in disk-manager, there are three options:

ntfs (Default driver)
ntfs (Unknow driver)
ntfs-3g (Read-write driver)

The middle option, "ntfs (Unknow driver)" is the one that is selected by disk-manager's auto configuration.  So which driver is the best choice?  I don't need write access, I only need to copy all my data off, verify that the data is intact and erase the old drive.  Are there pros and cons between the various driver choices I should be aware of?

Also, I'm wondering which program is the best option for copying all my data off and verifying that it is intact.  Should I just drag everything over in Nautilus or use a commandline command?  I have a large collection of digital photos and writing and it would be tedious to go through the collection one by one to make sure everything was copied safely.  Ideally it would be nice to create an MD5 or SHA1 checksum for each file and compare the checksums after copying, but I'm not sure if there is a program that will do this.

---

### Post by lindsay7 on 2009-05-15
I think you are making this too difficult. If you can read the windows drive in Ubuntu then all you need to do is copy and paste to the Ubuntu drive or directory that you want. You may need to mount the windows drive first but it should be found under "computer" in places.

---

### Post by Urnso on 2009-05-15
I have 160 drive in my laptop and what I do is take 30gig for win 30 for Linux and 100 for my music. I formatted the 100 as Fat32 Win is NTFS and Linux is Ext3. I just move my files from Linux drive to 100gig drive boot to Windows and I can access from there.
 
Now I'm not sure if this is the right way to do it but it works and I don't see any slowness or problems when copying from Linux to Fat32.

---

