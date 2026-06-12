---
title: "External Firewire Harddrive not working"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by Jabbapop on 2007-10-21
It worked fine in the live cd installer and the first few times I had my system running (can't remember if it was on when boot or hotmounted). 

anyway, when I plug the firewire drive into my firewire port, this is what dmesg tells me:

[  618.822922] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[  623.359575] ieee1394: Error parsing configrom for node 0-00:1023
[  623.359626] ieee1394: Node changed: 0-00:1023 -> 0-01:1023

i don't know what to do. there's no entry in my fstab or mtab for the drive. i'm not too familiar with the various procedures in establishing mounts manually (if that would even be relevant at this point.)


i looked through some of the threads on this forum already, and have tried removing and readding the firewire modules in modprobe but that didn't work. any help would be appreciated.

:guitar:

---

### Post by Jabbapop on 2007-11-03
This issue is still afflicting me. Restatement- my firewire hard-drive's functionality is sporadic. Sometimes it works, sometimes it doesn't. It's a bitter game of restart roulette. I depend on my firewire harddrive for the majority of my media files, and not being able to access them makes using my computer null. ergo, i should just boot into windows and forget i have a second partition.

ANGRY DO OR DIE LAST TEMPTATION OF THE LINUX  POST lol.

---

