---
title: "best file system for large partition holding large files"
date: 2008-09-08
forum: General Help
---

### Post by onesojourner on 2008-09-08
I am adding a hard drive to my computer and I need to know the best file system for my needs. The Partition will be large, most likely over 500 gigs. I do lots of video editing and I deal will some unnaturally large image files. Some of my files will be over 10 gigs in size. I have had problems in the past with permissions getting messed up on fresh ubuntu installs and I want to totally eliminate that. Right now I have 2 storage partitions one is ntfs and and one is ext3. I have had permission problems with the last 3 ubuntu fresh installs with the ext3 partition. I would like to have a file system that is laid back in that department. any user should be able to read and right this partition any time. I don't need any security and I want it to stay that way every time I put a fresh OS on the computer. I would like an open source file system but I will use ntfs if I have to.

---

### Post by HermanAB on 2008-09-08
XFS was designed to handle large video files.  However, JFS is good for that too.

Cheers,

Herman

---

### Post by starcannon on 2008-09-08
I read somewhere once that XFS is great for your situation. 

I'd probably do something like
```

/             ext3
Swap          swap
/home         ext3
/media/movies xfs

```

This lets you keep things like the OS and important personal files on the safest fs (actually ext2 is but who's ever heard of any linux FS blowing up unless poked with a sharp stick first?).

Anyway, thats the template I'd likely work with.

GL

Ha HermanAB beat me to it!

---

### Post by onesojourner on 2008-09-09
How stable is xfs if say power goes out while writing to the partition?

---

### Post by kpkeerthi on 2008-09-09
XFS is a journaling filesystem so you should be fine with abrupt power cuts.

---

