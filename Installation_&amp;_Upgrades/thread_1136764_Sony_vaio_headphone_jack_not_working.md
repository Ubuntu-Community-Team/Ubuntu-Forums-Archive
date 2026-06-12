---
title: "Sony vaio headphone jack not working"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by oskanaan on 2009-04-25
Hi,
I've upgraded my laptop yesterday to jaunty but i had this problem when plugging in my headphone the sound keeps on going out through the speaker only, i've read several threads about this and the following solution used to solve my problems on intrepid, which is adding "options snd-hda-intel model=vaio" to the /etc/modprobe.d/alsa-base.conf file. I've even tried OSS4 but I think it has the same problem. I was wondering if anybody faced the same issue? can it be solved?

Thanks

---

### Post by oskanaan on 2009-04-25
I've re-enabled alsa, still having the same probelm with the headphone, can anybody help me please?

btw, i dont have the switches tab in the volume control... is that normal?

---

### Post by yoasif on 2009-04-25
I would advise you to connect to the #alsa channel on irc.freenode.net (you can use xchat to connect) and ask for help. 

You should also [file a bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug") on launchpad concerning this so that it can be fixed in the next release.

---

### Post by oskanaan on 2009-04-25
Thanks for your reply,

actually i was finally able to fix this by removing the following from the file /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=vaio
options snd-hda-intel position_fix=1 model=3stack

i added these lines on intrepid because of this problem, it seems it was fixed in jaunty and i had to remove them after the upgrade for everything to work ok thanks god

---

