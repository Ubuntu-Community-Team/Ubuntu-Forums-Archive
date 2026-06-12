---
title: "Crashed Whilst Installing"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by GTgem on 2009-02-13
I downloaded Ubuntu today and installed it as a partition drive. But as it reached 98% completion my battery gave up! :eek:
Now although it does start fully I'm getting these errors when I try to update:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

How can I fix this?
Any help is very much appreciated.

PS: Sorry I've just registered and I'm probably going to get in trouble for posting this in a new thread but I couldnt find any other thread that really dealt with this issue.
Also I hope to become an active member here, not just a one time poster. 

Thanks again.

---

### Post by Taemojitsu on 2009-02-13
lol, just reinstall maybe :&#8203;P

I've reinstalled more times than I can count in the past two weeks because I keep messing stuff up.. >.< (bootloaders, proprietary drivers, packages from the wrong distribution which end up causing it to not load...)


If you did an automatic partition before, then this just means you have a chance to manually set partitions and understand what the different options are. You'll basically just need to set the root partition '/' if Swap already exists. google 'ubuntu partitions' if that part is confusing

---

### Post by GTgem on 2009-02-13
Thanks for the reply, even if it made very little sence to me!

I'll google in the morning how I would go about reinstalling everything, hopefully that'll solve it but I am after finding a thread with others experiencing the same problem, and no resolution, which is a little worrying.

---

### Post by Taemojitsu on 2009-02-13
you should be able to reinstall using the same CD you used for the original install. The only step that's different is the Partitions, where instead of an automatic resizing of things you have to select the partitions that are already created. Google 'manual partition ubuntu' might help, but basically you want to touch only the LINUX partitions (ext3 and swap) in a manual partitioning, and don't touch the windows partitions at all.

You can actually 'mount' or map the Windows partitions to a certain point in your linux file structure, but if you don't then they'll just show up as an extra drive just like a USB drive.

(NOTE: it might not automount and you might have to give HAL authorization to mount, but this is a one-time thing. You can avoid it by selecting a mount point for any Windows partitions. The default options are /dos and /windows, but you can do something else such as (mine) /media/thenameyouwanttogiveit . So it will automount; but unmounting internal media also has separate rules. If in doubt, don't bother to select a mount point for the windows partitions.)

---

### Post by GTgem on 2009-02-17
Thanks for your help. I've got it working perfectly now just un-installed Wubi from windows then reinstalled it again. So thanks again.:D

---

