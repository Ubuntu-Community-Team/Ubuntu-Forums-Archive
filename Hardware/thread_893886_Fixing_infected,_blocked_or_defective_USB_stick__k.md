---
title: "Fixing infected, blocked or defective USB stick / key"
date: 2008-08-18
forum: Hardware
---

### Post by alfrz on 2008-08-18
One friend of mine gave me his USB stick (1GB DT Mini Fun Kingston) because he had problems writing on it on XP .I guessed that because he uses it in many computers, it was probably infected by a virus so y naturally tried it on my computer with ubuntu.

To my surprise, I found the same problem that he did and so I proceeded to trick it so I could get it working.

Then tried to set up a new partition using GParted but I could do nothing to it so I started to search on the web and I found this thread: [http://ubuntuforums.org/showthread.php?t=683664](http://ubuntuforums.org/showthread.php?t=683664)

I tried cfdisk to wipe out the existing partitions and create a new one, but I get this message:

```
Opened disk read-only - you have no permission to write
```

So any change I try to do to the "disk" remains with no effect. dd also gives me the same message:

```
dd: opening `/dev/sdc': Read-only file system
```

fsdisk -l says this:

```
Disk /dev/sdc: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3936     1007600    e  W95 FAT16 (LBA)

```

And if I try to mount it:
```
$ sudo mount -w /dev/sdc /media/usb01
mount: block device /dev/sdc is write-protected but explicit `-w' flag given

```

The file attached to this thread is what I get after coding "ls > ls_info.txt" in one of the directories of the drive (this is the only one, I have no problem reading the rest). If you download this file (and if I can upload it) don't open it with the terminal, it can give a bit of trouble, I suggest oppening it with gedit or gvim.

[ATTACH]82039[/ATTACH]

---

