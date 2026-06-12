---
title: "[SOLVED] 8.04 latest kernel upgrade will not boot"
date: 2008-08-04
forum: General Help
---

### Post by kevinatkins on 2008-08-04
Hi all,

I have just applied the latest round of updates to Hardy on one of my machines, which included a kernel upgrade.

Now, the machine just hangs at 'Starting Up' (just after Grub) and won't boot. If I try booting with one of the earlier kernels, everything is fine.

Has anybody else seen this behaviour? I've got another machine waiting for updates to be applied but I don't want to do that if it's likely that it will also fail to boot afterwards!

Thanks in advance for any help.

---

### Post by TreeFinger on 2008-08-04
post boot.log from /var/log

---

### Post by kevinatkins on 2008-08-04
Hi TreeFinger,

Thanks for your reply. Unfortunately, I can't find boot.log in /var/log - there's just 'bootstrap.log', which appears to be very old and contains a heap of stuff relating to package management, or 'boot' - which is empty. I think what I'm going to do is to try verbose mode during startup and check whether any messages appear which might give a clue - if I come up with anything I'll post back.

---

### Post by Archmage on 2008-08-04
Are you sure that you are using the latest kernel (2.6.24-19) and not a buggy beta-release?

---

### Post by kevinatkins on 2008-08-04
Hi Archmage,

Yes, I was using 2.6.24-19 and the upgrade installed 2.6.24-20. Anyway, I checked some of the boot messages using verbose mode, and just after 'AppArmor Initialized', I was getting 'Failure registering capabilities with primary security module', then a few more messages before the system hung - the last message was 'Checking hlt instruction...OK'.

Well, I rebooted with 2.6.24-19 and after a few moments, the 'software updates available' icon appeared, so I clicked it and all of the updates which I'm sure I installed yesterday (including the 2.6.24-20 kernel!) were in the list... very, very strange. Anyway, I (re)installed the updates and now everything seems fine again. Most odd...

Thanks for your help folks - sorry to have perhaps been a bit hasty with my initial post.

---

### Post by Archmage on 2008-08-05
For me it sounds like you are using the proposed reopros. Kindly note that this isn't the suggested behavior, since there will be sometimes updates that wont work (like you just experiance).

---

### Post by kevinatkins on 2008-08-05
Hi Archmage,

I've just checked /etc/apt/sources.list on both machines, and sure enough, the proposed repos were in there... I can't remember why or when I did that but anyway, they have now been removed per your suggestion! Thanks for the tip - that's certainly what would seem to have happened.

---

