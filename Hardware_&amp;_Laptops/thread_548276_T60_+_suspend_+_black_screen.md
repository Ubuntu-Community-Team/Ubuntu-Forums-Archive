---
title: "T60 + suspend + black screen"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by analyzer on 2007-09-11
Hi

My system is a Lenovo Thinkpad T60 (Core2Duo, 2GB RAM, ATI Graphic Adapter)
Ubuntu Feisty Fawn

```
uname -a
Linux ubuntu-kb 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

```

The suspend to RAM is still working, but there is a problem if I want to wake up the laptop. The screen keeps black, I can't interrupt by CTRL + ALT + DEL. I have to switch the laptop off by the power button. 

Unfortunately there are a lot of known bugs:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/70602](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/70602)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104185](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104185)
...

I tried the workaround of thinkwiki:
[http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_ATI_graphic_chips_and_Intel_915.2F945GM](http://www.thinkwiki.org/wiki/Problem_with_display_remaining_black_after_resume#Solution_for_ThinkPads_with_ATI_graphic_chips_and_Intel_915.2F945GM)
It doesn't help. By the way, I can't set vga=0 in grub because I need vga=791 for my boot splash. 

Does somebody have a idea how to solve this problem?

Thanks a lot.

analyzer

---

