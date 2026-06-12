---
title: "USB Mp3 player file copying is extremely slow"
date: 2011-07-13
forum: Hardware
---

### Post by DBQ on 2011-07-13
Hi everybody.

I have recently purchased "Archos Key 4 GB MP3 Player with Built-In Micro SD Card Reader"

The file copying is in Ubuntu is very slow (takes like 2 mins to copy a 3MB file). I do not have this problem with other USB pendrives and what not. Also, when I let Windows 7 in VirtualBox (running on top of the same Ubuntu system on the same machine) to directly mount the player, Windows copies files very fast (and so do other Windows machines).  This is not the case in Ubuntu. When I do lusb I do not see any problems.  Is there any way to find/fix the problem? Any ideas about the possible causes?

NOTE: the interesting thing is that, after copying a file (the file is copied completely judging by the file size on the mp3 player drive), it would just wait for a while (doing what?).

I am using Thinkpad T500 and Ubuntu 11.04.


Thank You!

---

### Post by DBQ on 2011-07-16
bump

---

### Post by coffeecat on 2011-07-16
HI. I'm not sure I'm going to be able to help much, but I do have a couple of comments.

> **DBQ said:**
> NOTE: the interesting thing is that, after copying a file (the file is copied completely judging by the file size on the mp3 player drive), it would just wait for a while (doing what?).

With slow flash drives you often see the copy file progress bar get to 100% and then sit there for some time before the File Operations window closes. This is because the file has been completely copied to memory cache but it takes some time for the copy to flash drive to catch up. I've never watched the file size on the destination drive, but I guess what you've seen is to do with the same. I have an Archos Vision and copying is slower than with other USB flash drives but not nearly as bad as you are seeing. I'd assumed they use slower flash memory to keep costs down. The discrepancy you see between Ubuntu and virtual Windows is intriguing.

[noparse]Which kernel are you using? There was a bug in the kernel that came with 11.04 (2.6.3-38) that affected Archos Visions primarily. There was a thread recently where the OP was having problems with an Archos Key but somewhat different from yours iirc. Have you updated to the 2.6.38-10 kernel? This version solves the Vision issue. If you're not sure, this command from the terminal will tell you:

[/noparse]```
uname -r
```

---

