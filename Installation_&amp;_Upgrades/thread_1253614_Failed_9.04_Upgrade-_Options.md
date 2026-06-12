---
title: "Failed 9.04 Upgrade- Options?"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by kenhen93 on 2009-08-30
Hey All,

I tried upgrading to Ubuntu 9.04 via Update Manager from 8.10. It had some kind of postfix package installation failure and totally stopped the whole upgrade in the middle. After a reboot, it looks like I am missing the root file system. There is no etc/fstab. I am thinking the best way is to just re-install everything. I did not have a lot configured on the OS so its not a big deal BUT I have a software RAID 5 array that was seperate from my OS partitions that I absolutely want to get back.

I setup the current OS using the server CD and set the OS partitions to be mirrored, then a seperate RAID 5 array for media.

What is the best way to go about this?

Do you think its worth trying to recover the current OS?

Can I just go back through a OS setup using the server CD and reform my RAID 5 array without losing my data?

Thanks for any help.

---

### Post by ronparent on 2009-08-31
I'm not expert on software raid, but it appears that the server cd is equipped to recognize your raid 5 array. Your best bet may be to try to verify that raid5 array and assemble it from the server cd and then performing a raid1 install your OS partitions. The install, if the array can be verified, will probably automatically mount the raid5 on boot. Any expert views on this?

---

