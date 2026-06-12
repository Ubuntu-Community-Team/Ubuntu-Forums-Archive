---
title: "GRUB reconfigure - boot to wrong partition"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by DFreeze on 2009-03-04
I've used my laptop extensively for testing other distro's, so I have a number of partitions on them. Lately I've been settling on Intrepid, but the grub menu was still on one of the other partitions (the last installed distro).

So I thought I would fix that (every kernel upgrade didn't show up in the menu, I had to manually edit menu.lst on the other partition) and edited grub to point to my current partition (hda5) like so:
$ grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit

But after a reboot the computer boots up using the kernel from hda5, but fails to start X and drops me in the homedirectory of hda11 (the location of the last distro I installed)! Did I forget something (like update the initramfs or something)? How did this happen, and more importantly, how do I fix it?

---

### Post by Somiac on 2009-03-04
I don't know if your error is the same as mine but...
Whenever I startup my laptop now without my external HD plugged in it just says "Error Loading Grub 21" or something and stops and I have to power down the laptop plugin the ex hdd then I can goto windows vista through there. 

Any thoughts?

---

### Post by jaminux on 2009-03-04
Did you remember to adjust the boot order of the hard drives so that the one you installed grub to came first?

If you didn't you will be loading the old one which might have caused your problems...

---

### Post by DFreeze on 2009-03-04
Yeah, a quick Google on 'grub error 21' suggests that grub can't find the harddisk it is looking for. Probably the menu.lst is installed on the external drive. From the menu, grub can be told to load the OS installed on your first harddrive. 

So it looks like a 'long way round', but it is expected behaviour. 

The thing stunning me is that grub boots the kernel (including usplash and the whole shebang) from the right partition, but fails to load X and puts me in the homedirectory of a _different_ partition. I guess I should have told some other part of te bootprocess that I switched grub to another partition, but I don't know which part... Anyone?

---

### Post by Somiac on 2009-03-04
So, do I have to reinstall ubuntu? And when I do in the boot order list have my laptop HD first and then the external HD second?

And if I have to reinstall ubuntu do I have to do anything? or just reorder the boot sequence and then reinstall it?

Or is there something I have to do in Windows also before doing so

---

### Post by DFreeze on 2009-03-06
Hey Somiac, I don't know exactly how to do this, but maybe [these]("http://ubuntuforums.org/archive/index.php/t-664401.html") [links]("http://slashhome.wordpress.com/2008/11/04/recover-grub-bootloader-with-vista-xp-and-linux/") will help you along. I will try to update my initramfs this evening following [this guide]("http://bheesh.com/solution-initramfs-ubuntu-edgy-eft-problem-bug-67256"), to see if that will fix my issue. I will update here.

::UPDATE::

So I found the fix. It was simpler than I thought: the root=... part in GRUB was pointing to the wrong disk (DUH). These huge UUID numbers made it not so obvious to see (/dev/hdaX would be easily spotted to be right or wrong), but this took me a while to figure out. Checking the original grub menu.lst gave it away.

In any case, the computer boots normally again.

---

