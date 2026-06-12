---
title: "mounting error"
date: 2015-04-21
forum: Hardware
---

### Post by sniper8752 on 2015-04-21
I am trying to mount a failing corrupt hard drive.  I get an error about "The NTFS partition is hibernated".  I found [this post]("http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation") too late, but I am trying to follow these steps:
```

[LIST=1]
[*]Manually mount the filesystem in read only mode.

[LIST]
[*]Check to see if you have a mount point (folder for mounting your partition in) for your Windows partition in the folder /media using this command:
  ls /media

[*]If you don't see a folder for your Windows partition, you should create one with the following command:
  sudo mkdir /media/windows

[*]Next, mount the partition in read-only mode onto this folder with this command:
  mount -t ntfs-3g -o ro /dev/sda3 /media/windows
  Note that you should change /media/windows if your mountpoint is called something else.

[*]Now you will be able to view/open files on your Windows partition  using any program in Ubuntu.  However you will not be able to write  to the partition or modify any files as it is in read only mode.
[/LIST]
[/LIST]

```

I get an error like this:
```
fuse: failed to access mountpoint /media/windows: No such file or directory.
```

But when I check if this directory exists, it does.  Please help!

---

### Post by Vladlenin5000 on 2015-04-21
Any errors when mounting?

Obs.: The tutorial assumes you're attempting to mount a partition that has been already recognized as sda3 (partition 3 of the first drive, "a"). You should change it accordingly. For starters, if it's an external drive it probably would have a different final letter (b,c,d,..., etc.) because "sda" should be your internal drive where Ubuntu is installed.

---

### Post by ajgreeny on 2015-04-22
Where did this hard drive come from?

Internal or external?
Is it just a data partition or an OS system partition?

The error message tells you that it is in hibernation mode, but if you have a windows machine that you can attach it to, that should be able to mount it and then, very importantly, remove it safely using whatever way windows gives you nowadays to "Remove safely" and it should then mount in Ubuntu.

---

