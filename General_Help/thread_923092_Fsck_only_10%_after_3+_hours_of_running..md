---
title: "Fsck only 10% after 3+ hours of running."
date: 2008-09-18
forum: General Help
---

### Post by ebaniz on 2008-09-18
My situation is the following.

I was trying to get hibernation to work.  The system would hibernate properly but wouldn't wake up.  The only option I had left was cycling the power. Each time I did this, I noticed that mythbuntu would take a really long time to boot back up (I had a bunch of uuids in my fstab and I'm guessing it couldn't resume properly). On subsequent proper reboots, everything was fine.  The slowness only occurred when I cycled the power after a failed resume.  Anyhow, in my quest to get hibernation working I kept repeating these steps.  Unfortunately, I hit the 28 reboot count and fsck kicked in.  Now fsck is taking a ridiculous amount of time to complete. Since I can't disable fsck, it looks like I'm stuck waiting ~27 hours if this scales. Fsck is not stuck it is progressing albeit very slowly. I did try a shutdown -rf to skip fsck but that didn't work. I'm thinking because I Ctrl-C fsck and mounted / in read only, the shutdown command can't write /fastboot.  

So aside from using a live cd to edit my fstab.. are there any other options to fix the slow boot or perhaps to skip fsck?

Thanks,

---

