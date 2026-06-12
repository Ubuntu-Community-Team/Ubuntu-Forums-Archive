---
title: "Second SATA drive, unable to mount to mount-point"
date: 2008-10-05
forum: Hardware
---

### Post by AmunRa on 2008-10-05
I'm a little bit of a newbie with linux, so be gentle :) I'm adding a second SATA (500 gb) drive to a computer that already has an 80 gb drive with Ubuntu installed on it.  The 500 Gb drive is recognized by the bios, i've formatted it to ext3 with gparted, created a mount point in the media dir, and opened up the permissions with chmod 777.  Now, when i go to do mount 'sudo dev/sdb /media/vault' I get 'you must specify the file system type'

There's no data I need to save on the system in question, as I'm in the building/self-education process so I can wipe everything and start over with no tears shed.  Eventually I'll want to create another mount point and install & mount a 500 gb IDE drive from another system.  I'm only using Ubuntu, so no dual boot concerns either. 

Looking forward to your suggestions :)

---

### Post by linfidel on 2008-10-05
> **AmunRa said:**
> I'm a little bit of a newbie with linux, so be gentle :) I'm adding a second SATA (500 gb) drive to a computer that already has an 80 gb drive with Ubuntu installed on it.  The 500 Gb drive is recognized by the bios, i've formatted it to ext3 with gparted, created a mount point in the media dir, and opened up the permissions with chmod 777.  Now, when i go to do mount 'sudo dev/sdb /media/vault' I get 'you must specify the file system type' Obviously, that's not the real command that you entered; the question is, how close is it to what you entered?  For example, assuming you simply omitted the "mount" command after sudo, did you leave off the leading slash, or did you run it from the root directory?  

Also, you didn't seem to specify which partition to mount.

I believe what you wanted was "sudo mount /dev/sdb0 /media/vault".  This assumes you have only one partition on the 2nd drive.  If it's an extended partition, you may need something other than zero, such as "sdb1 or sdb3".  Take a look with gparted to see what the correct designation is.

---

### Post by AmunRa on 2008-10-05
Yes, the absence of mount was a typo in the post.  (oops)  The second drive is indeed one partition.  So the numbers after the drive name (sdb) denote which partition of the drive to mount?  And 0 is the default for the 1st partition or the entire drive if there are no others?  Do I need to do anything with partitions for the main drive?

---

### Post by linfidel on 2008-10-05
> **AmunRa said:**
> Yes, the absence of mount was a typo in the post.  (oops)  The second drive is indeed one partition.  So the numbers after the drive name (sdb) denote which partition of the drive to mount?  And 0 is the default for the 1st partition or the entire drive if there are no others?  Do I need to do anything with partitions for the main drive?I don't know for sure whether you need to specify the number for a single partition or not - but I think it would be a good idea to do so anyway.  In the future, if you add more partitions, you might miss this, and have problems.

No, you shouldn't have to do anything with the main drive.

When you look at the 2nd drive, is there only one partition, sdb0?

I don't have any more ideas right now.

---

