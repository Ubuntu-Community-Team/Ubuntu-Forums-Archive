---
title: "Internal Hard Drive Unreadable"
date: 2009-01-02
forum: Hardware
---

### Post by laxwrestler on 2009-01-02
Ok need some help with this one.  I have 8.10 installed on a 300gb hd on my computer.  Additionally I have a 80gb internal hd formatted as ntfs.  It is ntfs because I just helped my dad switch from windows to linux.

The 80gb hd shows up in nautilus and will mount when you double click on it to /media/disk.  Once it is mounted you can view the filesystem however it is not readable.  Attempting to copy, open, or do anything else with the files results in a permissions error.  I have tried mounting from the fstab file as ntfs-3g with rw permissions with no luck.  I have tried "sudo nautilus" to open a file browser as root and open files with no luck. "sudo cp" fails with permissions errors as well.

I need some help with this as this drive has a bunch of backup files that my dad needs to access.  If we can just get the files off of it I can reformat it to ext3 for him.  I believe the problem may be due to the drive not being properly unmounted in windows however we no longer have a windows install to try to boot and unmount properly.  I was thinking I could mount it in virtualbox and then unmount it properly from there but it doesn't look like I can mount an actual hard drive in virtualbox.

If anyone has some help with this I would greatly appreciate it.

---

### Post by Kilz on 2009-01-02
> **laxwrestler said:**
> Ok need some help with this one.  I have 8.10 installed on a 300gb hd on my computer.  Additionally I have a 80gb internal hd formatted as ntfs.  It is ntfs because I just helped my dad switch from windows to linux.

The 80gb hd shows up in nautilus and will mount when you double click on it to /media/disk.  Once it is mounted you can view the filesystem however it is not readable.  Attempting to copy, open, or do anything else with the files results in a permissions error.  I have tried mounting from the fstab file as ntfs-3g with rw permissions with no luck.  I have tried "sudo nautilus" to open a file browser as root and open files with no luck. "sudo cp" fails with permissions errors as well.

I need some help with this as this drive has a bunch of backup files that my dad needs to access.  If we can just get the files off of it I can reformat it to ext3 for him.  I believe the problem may be due to the drive not being properly unmounted in windows however we no longer have a windows install to try to boot and unmount properly.  I was thinking I could mount it in virtualbox and then unmount it properly from there but it doesn't look like I can mount an actual hard drive in virtualbox.

If anyone has some help with this I would greatly appreciate it.

You might want to post the contents of your /etc/fstab file, I have a feeling thats where the issue is. You should also look at the permissions tab of one of the files you cant read and see who owns it.

---

### Post by laxwrestler on 2009-01-02
relevant fstab line 
```
#sdb2 80gb hardrive
UUID=D0F89D10F89CF646 /media/disk ntfs-3g defaults,rw 0 0
```

The permissions says that the user root, group root, and others all have read and write access.  This is true for both files and folders  in /media/disk/.

Additionaly, performing "sudo chown USER /media/disk/FILENAME" does nothing but does not give any errors.

EDIT:
Also, it is possible to create new files on the disk and modify them easily just not any files previously on the disk.

---

### Post by laxwrestler on 2009-01-02
Update:

I figured out how to mount a physical drive using the proprietary virtualbox, however the mount fails due to another permissions error :(.

I'm hoping someone here can help before I try reinstalling windows just so I can attempt to properly unmount the drive and see if that fixes the problem.  Reinstalling windows is a giant pain in my ***.

Anyone?

---

