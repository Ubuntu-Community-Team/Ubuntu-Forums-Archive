---
title: "partition not recognized?"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by rubisco on 2009-10-09
Well, to be brief, I can't boot into Ubuntu now, though I could before. Now here's my situation:
1. I install Ubuntu 9.04 directly from CD after Vista got installed. Then I use easyBCD to make Vista manage the booting choices, and it worked successfully.
2. Then I installed ext2fsd, after several trials I can see and read my Ubuntu disk now. I didn't try to write anything with ext2fsd, but I CHANGED THE LABEL FOR UBUNTU PARTITION IN VISTA. Then when I try to reboot again, whatever I choose in GRUB, it would show "uuid=xxxxxxxx" and says file not exist (or location not exist? I can't remember), then jump back.
3. I wonder whether changing  label would affect, so I changed it back to blank in Vista (I still can read everything there), but still no luck. Then I try to find whether uuid has been changed, thus under grub I type uuid, but only Windows partitions are listed. I boot from the live cd, and find (1) my windows partitions are recognized but Ubuntu one is not, both in file browser and in "ls -l /dev/disk/by-uuid"; (2) the partition editor can't recognize any partitions on my HD, also when I attempt to reinstall Ubuntu it would tell me that no other system has been installed but apparently I have Vista there.

So now I can't boot into Ubuntu nor can I do a reinstall, well, unless I delete the Ubuntu partition in Vista I guess. I've done a lot of searching, but can't solve it still. Any suggestions would help. Thank you everyone!

---

### Post by tpjk on 2009-10-09
did you use the wubi installer to install ubuntu inside vista or did you install ubuntu to a different partition?

---

### Post by rubisco on 2009-10-09
> **tpjk said:**
> did you use the wubi installer to install ubuntu inside vista or did you install ubuntu to a different partition?

I didn't use WUBI. I just specify the amount of HD to use when installing Ubuntu, so I think it must be a different partition (same disk, though).

---

### Post by tpjk on 2009-10-09
> **rubisco said:**
> ... the partition editor can't recognize any partitions on my HD, also when I attempt to reinstall Ubuntu it would tell me that no other system has been installed but apparently I have Vista there.

please post a screenshot of your partition editor.

---

### Post by rubisco on 2009-10-09
Ah, sure. I'm not at home right now. I'll post them within 2 hours. Thanks in advance:)

---

### Post by rubisco on 2009-10-10
I can't mount any of my disk (nor my USB drive) under live CD mode so I can't get the image out (my laptop's wireless can't work under live CD mode either). However it only says all my partition is unallocated and my disklabeltype is unrecognized...

---

### Post by rubisco on 2009-10-10
Ah, Thank you everyone. It's much simpler than I thought. When I use ext2fsd, it sets the partition type of my Ubuntu partition to 85(Linux extend) instead of 83(Linux). I set it back and now everything is fine:)

---

### Post by tpjk on 2009-10-10
well, congrats on working that out. :)

you should mark this thread as SOLVED now.

---

