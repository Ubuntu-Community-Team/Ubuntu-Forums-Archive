---
title: "Weird issue with USB external HD crash"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by houshuang on 2007-08-10
I have a really weird issue and I'd appreciate any help, even pointers to how I could better diagnose the issue.

I have a 400 gb external WD usb HD, hooked up to my Samsung R20 laptop, and I am trying to run a Ruby script that does a bunch of analysis and compression of huge files on the external HD - the script is supposed to take about eight hours. Midway in the process, the ruby script crashes... well, not really crashes, it freezes. Ie it just stops, and won't take any input, I can't even kill it from any other terminal. To eliminate problem sources, I run it from bash in a single user login (no X)... 

At first I thought that maybe my program was poorly designed, uses too much memory etc, but I don't think so. It doesn't core dump or crash or anything, the shell it's in is completely inresponsive, but the computer works great. Here's the really freaky thing though - whenever another shell tries to access that drive - say I do a ls -l /media/elements/, or even type in cd /media/elements and do a tab (it needs to check the disk to give me options for tab complete), that virtual terminal completely freezes, and is completely unavailable. This happened on three different virtual terminals.

SO it seems taht something is really wrong with the usbdriver? Or? There are no messages in dmesg, etc... I have no idea what to do about this, and it's driving me nuts. I had the drive formatted as vfat, but I thought that was part of the problem since I had so many small files, so I reformatted it as xfs. No change.

any help appreciated!
Stian

---

