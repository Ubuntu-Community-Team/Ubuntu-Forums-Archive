---
title: "Help me access second hard drive"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by johndyoung on 2009-05-30
I installed two identical 320 gig hard drives and setup the raid on the motherboard controller and then installed Ubuntu.  When I rebooted, it would not load, and then I did some searches and found out the problems with a raid with Ubuntu.  So I disconnected the raid and reinstalled Ubuntu on the first drive.  I then tried to access the second drive and can't do it.  I partitioned and formated it with gparted.  

When I try to mount the drive, I get the following message "unknown filesystem type 'promise_fasttrack_raid_member."

Can someone please help me solve this problem?

Thanks.

John

---

### Post by logos34 on 2009-05-30
you disabled raid mode in the Bios?

---

### Post by johndyoung on 2009-05-30
Yes, I disabled RAID in the BIOS.  The RAID controller is even a separate connector from the normal hard drive controller.  So I now have the drives hooked to the normal hard drive controller.

The solution to the problem is to somehow remove the data the promise controller put on the hard drive.  Even though I partitioned and formated the drive with Ubuntu, the data the Promise Controller put on it is still there.

---

### Post by ronparent on 2009-05-30
You are correst. I don't know if that is the problem. But assumming it is and you still have dmraid (the fakeraid software) still installed, use the command **sudo dmraid -E** to erase the metadata. If you are not using it you should also uninstall dmraid with **sudo apt-get purge dmraid**. This should clear the disk for normal use.

---

### Post by logos34 on 2009-05-30
> **ronparent said:**
> If you are not using it you should also uninstall dmraid with **sudo apt-get purge dmraid**. This should clear the disk for normal use.

Does raid0 really offer substantial performance gain for *average desktop usage*?  How much faster do apps really launch, anyway (which seems to be the main attraction as I see it)?  Just curious about people's real experience with it.  What I've read seems to suggest it's a mixed bag and the benchmarks sometimes counterintuitive.

---

### Post by ronparent on 2009-05-30
logos34: I've seen claims of having measured a doubling of the through put with a raid0. I personaly doubt that much improvement. And even if it is, I'm beginning to have doubts the the increased system complexity makes it worthwhile to the average user (including myself}.

---

### Post by johndyoung on 2009-05-30
I never had dmraid installed.  I thought the motherboard Promise controller was a hardware solution that would work with any operating system so that is why I tried it.  When it didn't work and I read the posts about the problems with RAID in Ubumtu, I just abandoned it all together.

So it was the Promise controller that put that data on, not dmraid.

---

### Post by johndyoung on 2009-05-30
I wanted to install for mirroring not quicker perfromance.

---

### Post by johndyoung on 2009-05-30
I tried this command, **sudo apt-get purge dmraid**..  It said that dmraid was not installed.

Anyone else have any ideas?

---

### Post by ronparent on 2009-05-31
I'm too unfamiliar with mddam to say for sure. It probably can accomplish the same objective - ie erase the metedata on your dirvers,

---

