---
title: "Moving Root Partition"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by theonhighgod on 2009-06-24
Firstly I would not recommend following this how too, instead I would recommend:

[LIST=1]
[*]Loading Synaptic (need to install in kubuntu)
[*]go file -> Save Markings as
[*]Tick the box marked "save full state, not just changes"
[*]Save the list of installed files in a safe place not on your root partition 
[*]Re install the latest version of k/x/ubuntu with out wiping home
[*]install or run synaptic
[*]Load saved state and click apply to reinstall all your old programs
[/LIST]

Now Maybe you can't download all your packages again if your stuck on a low connection in which case I suggest backing up the contents of "/var/cache/apt/" then reinstalling as above but before loading your saved state restore the backed up version of "/var/cache/apt/" I have not tested this method on a version of ubuntu since about 2005 so probably best to go to a friend's house with a good connection.

So failing those methods if you are sure you still want to try to move your root partition then read on. I have not tried this method since around version 8.04 maybe even 7.10 so no Guarantees

[LIST=1]
[*]First back up files encase it fails
[*]Repartition  and create new root partition the same size as original
[*]copy root to new partition with "dd"
[*]load boot cd and chroot into moved root partition 
[*]run grub-install from chrooted root partition 
[*]edit fstab on new root partition 
[*]edit /boot/grub/menu.lst on new root partition 
[*]reboot and hope
[*]If all worked out now is the time to resize the new partition using the boot cd 
[/LIST]

If this works for you please contribute to this thread and fill in any gaps....

---

