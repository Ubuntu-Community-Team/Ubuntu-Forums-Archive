---
title: "Drive space suddenly all gone, need to check FAT errors"
date: 2008-11-01
forum: General Help
---

### Post by stozi on 2008-11-01
Hi. Yesterday I realised my case was not grounding the computer. I noticed this because there was static in the audio and my USB disk kept skipping while downloading some torrents. I traced a wire from all the screw holes to the power jack. This solved the 2 previously mentioned problems. I believe I was left with massive errors on the disk though. When I checked how the torrents were doing after lunch, I had zero disk space. After a bit of struggling to be able do anything on the machine, I traced most of the new bytes to /var/log/kern.log & syslog. I just deleted these, assuming new ones would be automatically generated in their places, which seems to so far only be true for syslog. I am still missing about 300Mb of empty space though, that is a lot for my system & I'd really like it back. I also want to know how I can fix the file system on my external FAT32 disk. 

If I delete everything in /var/log will the system survive?
Is there a command for checking a FAT32 at will?

Thanks!!!

---

