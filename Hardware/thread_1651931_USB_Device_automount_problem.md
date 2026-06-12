---
title: "USB Device automount problem"
date: 2010-12-23
forum: Hardware
---

### Post by KamiKazeKenji on 2010-12-23
Everything was fine when I freshly installed Ubuntu a couple months back, but somewhere along the line something went wrong. When I plug in some of my USB storage devices, they do not automount, and I get an error when I try to mount it. Some devices do automount (like my camera, and a few of my flash drives), but some storage devices (like my Seagate HDD) do not.

It's a hassle to mount from the terminal every time I connect something. How would I go about fixing this?

---

### Post by mikewhatever on 2010-12-24
You probably want to run filesystem checks on those devices. Use the Disk Utility under System->Administration.

---

### Post by KamiKazeKenji on 2010-12-25
Filesystem check revealed that the filesystem (on my Seagate drive) is NOT clean.

Also, this is the error I get when I try to mount: ```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed
```

What can I do from this point?

---

### Post by Fafler on 2010-12-26
Clean it. Ubuntu won't automount unclean NTFS filesystems. Theres a program called ntfsfix and if it doesn't work, you have to use a Windows machine.

Did you run something like mount -a to get that error?

---

### Post by KamiKazeKenji on 2010-12-26
Just to be sure, does running a program like ntfsfix on my hard drive have a chance to corrupt my data? I remember chkdisk screwed up one of my flash drives pretty bad a while back.

I got that error after I attempted to mount it from the disk utility. It mounts successfully when I mount it from the terminal e.g. "sudo mount /dev/sdb1 ~/mount".

---

### Post by Fafler on 2010-12-26
I guess theres always a chance of filesystem corruption. Chkdsk should be the better choice.

---

### Post by KamiKazeKenji on 2011-01-07
The problem seems to have fixed itself... interesting. I'll make sure to properly disconnect my drives from now on; not just unmounting them but powering them off.

Thanks for your help everyone, this is solved... for now.

---

