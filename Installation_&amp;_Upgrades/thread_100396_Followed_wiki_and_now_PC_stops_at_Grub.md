---
title: "Followed wiki and now PC stops at Grub"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by cpharvey on 2005-12-07
Well I thought I'd give it a try so I followed the wiki on installing Ubuntu on a fakeraid system [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

All seemed to go well except I had trouble with the grub piece which I thought I'd eventually worked out.

In short I have Windows XP professional on my 1st partition and Ubuntu loaded on subsequent partitions.

Now when I boot my PC i'm left with a grub shell and have no idea how to get either Ubuntu to load or get Windows to load. I thought I was going to get a grub prompt that would ask me which one to load!

Help!?!

---

### Post by cpharvey on 2005-12-07
Well i partly sorted out the issue. Turned out to be a missing menu.lst file which I created and now have the option Windows or Ubuntu.

next problem is that Ubuntu doesn't completely load. It goes quite a way and then get's to the point of initializing /dev and says:

Begin: Mounting root file system ...
Begin: Running scripts/local-top
[4294689.900000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
/scripts/local-top/dmraid: 3: dmraid: not found
/scripts/local-top/dmraid: 3: dmraid: not found
blah blah...

Any ideas why?

---

### Post by M_Cheevy on 2005-12-14
In reading over a number of howto's to get debian installed on my sil_3114 based sata fakeraid0 array with a couple of other copies of windows, I noticed something missing on the wiki...   a couple of the other articles I read indicated, when setting up grub by going into the shell, start it with the option: --device-map=/dev/null (as one howto put it, "or be a fool")

Hope that helps...

---

### Post by realriot on 2006-01-04
[QUOTE=cpharvey]
Begin: Mounting root file system ...
Begin: Running scripts/local-top
[4294689.900000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
/scripts/local-top/dmraid: 3: dmraid: not found
/scripts/local-top/dmraid: 3: dmraid: not found
blah blah...
Any ideas why?[/QUOTE]

if you followed the fakeraidhowto step by step you have the problem that dmraid is not installed within the chroot environment and the update-initramfs does not find the dmraid binary... apt-get install dmraid and then rebuild the initramfs... 

then you'll get further and have other problems... kernel panic with circular dependancy (or something like that). can't find the problem and hoping for help so that we can fix the howto.

---

