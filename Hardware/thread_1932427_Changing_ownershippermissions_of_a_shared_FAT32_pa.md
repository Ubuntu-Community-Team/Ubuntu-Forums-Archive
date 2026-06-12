---
title: "Changing ownership/permissions of a shared FAT32 partition"
date: 2012-02-27
forum: Hardware
---

### Post by chellrose on 2012-02-27
I have a dual-boot laptop, Ubuntu 10.10 and WinXp.  I have a shared FAT32 partition, which I've called "/osshare", accessible by both Linux and Windows.

Right now, the ownership is shown as root and the permissions are drwxrwx---.  I'd like to change ownership to my own username, not "root", but all combinations of "sudo chown" and "sudo chmod" fail with an "Operation Not Permitted" error.

I tried changing the mount point to a subdirectory of my home folder, and adding a "umask=000" to my /etc/fstab (as described [here]("http://www.linuxforums.org/forum/miscellaneous/53527-cant-change-permissions-mounted-fat32-partition.html")), but to no avail.

Right now, I seem to be able to edit documents within the shared partition, which is good, but I can't use a picture from it as my desktop background (hence the wish to change ownership).  How would I go about doing this?

Thanks!

---

### Post by sudodus on 2012-02-27
If you can read and write files (documents) pictures etc, I think everything is good. If not, we should change the mounting of your shared FAT32 partition.

I suggest that you copy the picture you want to use for background to your linux partition (for example to your Pictures or Photos folder), because then it will be available at boot, before the other drive will be mounted.

---

### Post by ahallubuntu on 2012-02-27
It's not possible to set permissions or ownership of files by Linux in a Windows filesystem.  But don't worry about it, as you are clearly able to access everything.

FYI, FAT32 works great with one big exception: you can't store files larger than about 4GB on it.  In Windows, NTFS (which has journaling built in) is a far superior filesystem to FAT32; journaling allows better recovery from errors.  You wouldn't have the 4GB limitation with NTFS.  Ubuntu of the last few years works well with NTFS and journaling is at least partially supported.

---

### Post by chellrose on 2012-02-27
Thanks! I'll try copying the picture to a Linux folder.  I was trying to avoid having 2 copies of the same file around, but I'll get over it. :)

I must have read an old "how-to" on sharing those partitions, because my understanding was that Ubuntu didn't support NTFS.  I'll try it now, though.  If I just reformat the partition as NTFS and update my /etc/fstab appropriately, should that do the trick?

Also, just out of curiosity, what do you mean by journaling?

Thanks again! :)

---

### Post by sudodus on 2012-02-27
> **Sissy13 said:**
> Thanks! I'll try copying the picture to a Linux folder.  I was trying to avoid having 2 copies of the same file around, but I'll get over it. :)

I must have read an old "how-to" on sharing those partitions, because my understanding was that Ubuntu didn't support NTFS.  I'll try it now, though.  If I just reformat the partition as NTFS and update my /etc/fstab appropriately, should that do the trick?

Also, just out of curiosity, what do you mean by journaling?

Thanks again! :)

***Backup***
Yes, but of course, your files will be lost unless you back them up before reformating.

***Journaling*** means that information is saved about what has been done recently. See [[COLOR="Red"]_http://en.wikipedia.org/wiki/Journaling_file_system_[/COLOR]]("http://en.wikipedia.org/wiki/Journaling_file_system")

---

### Post by ahallubuntu on 2012-02-27
> **Sissy13 said:**
> Thanks! I'll try copying the picture to a Linux folder.  I was trying to avoid having 2 copies of the same file around, but I'll get over it. :)

I must have read an old "how-to" on sharing those partitions, because my understanding was that Ubuntu didn't support NTFS.  I'll try it now, though.  If I just reformat the partition as NTFS and update my /etc/fstab appropriately, should that do the trick?

I've been using NTFS in Ubuntu for years - works great except for one thing: huge files (4GB+) can take a long time to copy and load down the CPU.  Of course, you couldn't store them at all in FAT32.

Yes, as noted above, as long as you backup your files first (because formatting will erase them), just re-format the partition and add it to your fstab .  Use its UUID to mount it (to find out the UUID of the partition after you format it as ext4, type "sudo blkid").  After you edit the fstab, do "sudo mount -a" to check that the fstab is correct, otherwise if there's an error in the fstab you won't be able to boot later.

---

