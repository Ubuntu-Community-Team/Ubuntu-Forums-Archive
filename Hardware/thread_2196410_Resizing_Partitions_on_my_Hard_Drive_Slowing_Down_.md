---
title: "Resizing Partitions on my Hard Drive Slowing Down Performance"
date: 2013-12-29
forum: Hardware
---

### Post by Clarenceadams on 2013-12-29
I have googled like crazy for information pertaining to this issue but the only solutions I could find was "Clear temporary files and clean your registry if you're running Windows." I am running a Dual Boot with Windows 7 and Ubuntu 12.04 and ever since increasing my Ubuntu partition with PartedMagic by 60GB Windows AND Ubuntu have been performing rather slow. Since they're both performing slow I doubt the Windwows 7 registry/temporary files are affecting how Ubuntu performs. I also know my Hard Drive is in good health because I used Smartmontools in order to test it. I've checked the Windows filesystem and Ubuntu's filesystem. I have no clue how a partition resizing could be causing both OS's to perform worse since I didn't even touch the Windows partition.

Has anyone else had this problem and if so how should I go about fixing it? I am dreading reinstalling both OS's but I really don't even know where to start with fixing this.

Thanks in advance for any help or advice and if you need any aditional information at all please ask.

---

### Post by oldfred on 2013-12-29
Windows can be slow if you just make it too small. It needs about 30% free space and at 10% free will be very slow. You just about cannot do a defrag in Windows with 10% free as it has no working room.

Not sure about Ubuntu.

RAM is important for systems to work. Are there any issues. I might run memory tests.

---

### Post by Clarenceadams on 2013-12-29
Thanks for the response oldfred, it never occured to me to run a memory test. The Windows partition has more than 30% free and I didn't shrink it when I resized I only enlarged my Ubuntu partition. I'm going to run memtest86+ and see if it encounters any errors. I'll report back with the results. Also I should add that my laptop has 4GB of RAM so I don't think the amount of RAM would be the issue but bad RAM could definitely be the culprit. Thanks again for the help!

---

