---
title: "Intellistripe 65 driver kernel panic"
date: 2010-09-23
forum: Hardware
---

### Post by allan8904 on 2010-09-23
Hi,
Previously we ran a 2.6.23 Linux kernel on our systems. We have now  upgraded to a 2.6.32 kernel and are in the process of testing to make  sure everything works. We have a driver for a Magtek Intellistripe 65  that was previously working in the 2.6.23 kernel. Originally it didn't  want to be loaded into the 2.6.32 kernel at all. I had to make some  changes to the code (ie replace kill_proc and other functions that have  since been removed/replaced) and now when the card is removed the system  freezes. I have a feeling that it could be to do with changes to  usb-core, but i'm not sure. I looked through and diffed the kernel for  changes to usb-core, but i cant see any earth shattering changes to it,  so i believe it still should be working fine. I've tried my modified  version on the 2.6.23 kernel, and its all working fine, so it wasn't my  changes that broke it. Does anyone have any ideas as to why this could  have happened? Or possibly know of a driver that works on the 2.6.32 kernel?
Thanks,
Allan

---

