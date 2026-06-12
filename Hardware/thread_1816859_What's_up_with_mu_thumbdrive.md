---
title: "What's up with mu thumbdrive?"
date: 2011-08-02
forum: Hardware
---

### Post by afajknaz on 2011-08-02
I noticed that in Windows my Mirandia died quietly. Restart -> crash. I tried its repair tool on the database, but got some cryptic Windows error when trying to read it.
I safely removed it, unplugged, plugged again. Whenever I try to access it in Windows, I get the error; found a lot of info about it, but apparently people get it in different situations.
The error message was:
```
---------------------------
Windows - No Disk
---------------------------
Exception Processing Message c0000013 Parameters 7c7df5f8 e80fdcf8 7c7df5f8 7c7df5f8
---------------------------
Cancel   Try Again   Continue   
---------------------------

```Anyway, I noticed that drive properties show its capacity as 0. GUI checkdisk dies immediately when ordered to do something with it, command line one shows:
```
Cannot open volume for direct access.
```On to Linux.

First, automount doesn't work.
I tried fsck.vfat:
```
open: No medium found
```badblocks:
```
No such file or directory while trying to determine device size
```
Without much hope, I tried testdisk too, but it doesn't list it among other drives.

Any chance to bring it back alive? I have a backup less than 2 weeks old, but it's still quite old and I'd rather not loose the data...

---

