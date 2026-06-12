---
title: "Samsung SSD Install Now What?"
date: 2012-10-26
forum: Hardware
---

### Post by smuggly on 2012-10-26
I just installed Xubuntu 12.10 on a sata 3 samsung ssd. I used default hard drive options. I have searched around & understand i need to disable journaling? Is this True? Also i have a 2nd mech. HD i need to change permissions on Is changemod 755 the right choice for this? Thanks
Smuggly

---

### Post by oldfred on 2012-10-26
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

This was pretty much all I did:
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

Do not just do chmod on other drive if not sure what you are doing. Is parition in Linux format. Ownership nor permissions are supported by Windows formats.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by smuggly on 2012-10-26
Yea 2nd drive i just formatted using gparted and ext 4 file system. Whats the noop scheduler? Thanks

---

### Post by oldfred on 2012-10-26
There are several schedulers. The default is designed more for rotating drives. Not sure if they now have changed to cfg or not. Recommendation on noop was from a year or two ago.

[http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)

To see what you are using:

fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq]

---

### Post by smuggly on 2012-10-26
OK i will try when i get the config all set. i got the hdd (Mech. One) all permission set.

---

### Post by smuggly on 2012-10-27
I ran sudo tune2fs -O ^has_journal /dev/sda1 and it returned a "bad magic number couldn't find superblock or something to that effect. also i added the discard,noatime option to fstab to sda. Is it possible journaling be left on? is not this one of the main reasons we want ext4 in the 1st. place? I've read alot of stuff on this the last 24 hrs. It seems the configurations aren't keeping up with the technology. (ssd getting better) I would like you're opinion on this oldfred & anyone else please. Thanks smuggly

---

### Post by oldfred on 2012-10-27
The  argument was you did not need a journal on a smaller partition and it reduces writes if you do not have one. Why boot partitions are usually ext2 historically even with rotating drives.
With a journal, fsck is quicker  and repair or recovery is more likely. Why we use ext4 for larger partitions.

So with SSD and just a partition with system files journal does not add much and not having it reduces writes. But now they say the newer SSDs have lives not all that different than rotating drives so it does not matter.

I have an OEM/house brand (low cost) SSD, and have it configured with boot files and only user settings from /home. All my data is on a rotating drive. So I do not think journal adds much and if not having it increases life a bit, I will run without journal.

Or I do not really know. :)

---

### Post by smuggly on 2012-10-28
Thank You sir, For You're Help. Smuggly

I thought i would add that after much serching and though . I went with just the trim enabled ande fstab otions dscard and noatime. Time will tell if i am right or not.
I will post back if i have any problems with my samsung ssd.

---

