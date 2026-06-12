---
title: "Problem writting to external."
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by -RYknow on 2007-08-12
I've been having some issues with an external HD that I have. It's a Vantec Nexstar 3 with a Western digital 250 gig HD. The drive was originally setup with an NTFS File system, and loaded with music, TV Shows, and various Windows programs (not installed on the drive, just stored there). When I plug the drive in, it shows up on the desktop, and I can look at anything or play anything on the drive, but I was having issues with writting to it...and deleting files from it. 

I did some research, and it seems a lot of people have issues with NTFS and Linux. I installed Gparted, and formatted the drive as ext3 cause I just wanted more storage. I also thought they by formatting the drive, it might eliminate the issue of writting to the drive. After formatting, I'm still having issues where I can't write to the drive. 

When I go to the properties/permissions, all of the pull down menus are greyed out, so I can't change them. It says the owner is root, and the group is root. If I go into terminal, type su root, then my pass...I still have no luck with being able to change the permissions. 

Hopefully someone can help me out here. I'm still very new to Linux, but it's been fun learning something new. Any help would be great! Thank you! 

-RYknow

---

### Post by merlinus on 2007-08-12
Post results of:

```

cat /etc/fstab
sudo fdisk -l

```

with the drive plugged in.

-merlin

---

### Post by -RYknow on 2007-08-12
> ryknow@LinuxBox:~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18890   151733893+  83  Linux
/dev/hda2           18891       19457     4554427+   5  Extended
/dev/hda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   f0  Linux/PA-RISC boot


Thats what I get. I'm still not able to write to the drive, or change the permissions of the drive?

-RYknow

---

### Post by merlinus on 2007-08-12
What about output of:

```

cat /etc/fstab

```

as per my previous post.

-merlin

---

