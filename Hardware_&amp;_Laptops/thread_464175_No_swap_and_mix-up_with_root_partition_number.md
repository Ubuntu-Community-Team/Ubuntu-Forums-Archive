---
title: "No swap and mix-up with root partition number"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by uziel on 2007-06-04
I have an interesting problem with my root and swap partitions. The idea is that, Windows partitions aside, there's a 9G root partition and 750M swap partition. It worked like that some time ago, but after I did something bad (I don't remember what exactly, it was so long ago) weird things started to happen.

The 9G partition is /dev/hda6, 700M - /dev/hda7. Nonetheless, /dev/hda7 is listed with mount point / in /etc/fstab. Other files/apps that store/list partitions and filesystems also state various things. For example, the disks-admin  app in old (6.06, in the meantime I upgraded to 6.10) Ubuntu did show /dev/hda7 as / with its 700M space (I don't remember how full it appeared) and /dev/hda6 as swap space, with its 9G space greyed out.

"Of course", I have no swap. I was rather unaware of it until earlier today, and (except for some moments, when running Open Office, The Gimp, Firefox and maybe some more bloated programs, Xorg had to be killed) didn't notice any greater inconveniences. Anyway, today I tried to do something about it and even accidentally (due to the mess mentioned above) mkswap'ed my root partition, so I had to rescue it with e2fsck (luckily it succeeded).

Does anyone have any clue? I couldn't find my problem on this forum/the Net, maybe because I can't even describe my problem briefly and precisely; all "related" problems with no swap seem to far away.

Personally, I'm not interested in having these partition numbers in place. I just want to have my swap back. I'll be happy to provide any helpful output/content. I'm running Acer Aspire 3002 WLMi with Sempron 2800+, 512M RAM and 80G HDD.

---

