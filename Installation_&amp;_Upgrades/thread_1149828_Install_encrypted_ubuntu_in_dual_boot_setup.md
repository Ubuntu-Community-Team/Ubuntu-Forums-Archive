---
title: "Install encrypted ubuntu in dual boot setup"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by XCan on 2009-05-05
Lately, I've seriously been considering to install *nix on my last PC, although in a dual boot setup. My question regards whether or not the dual boot setup will work if I attempt to install ubuntu using the alternate setup cd.

If yes, then are there any tips on how to not break anything?

I was considering to first manually partition my current disk (XP installed) and use the alternate cd to install the encrypted ubuntu on the newely created partition.

Thanks in advance.

---

### Post by dabang on 2009-05-05
Just try to not kill your Windows partition during setup! ;-)
There is no big difference between Desktop and Alternate install. It'll find your Windows installation and add it to grub as usual. If you want encrypted filesystems/volumes, remember to create a separate partition for /boot.

---

### Post by XCan on 2009-05-05
Thanks for the quick answer. Good thing you reminded me of the /boot partition. My partition knowledge is a bit rusty, but if I recall correctly, it is enough to only let /boot be a primary partition and / & swap be logical partitions right?

---

### Post by dabang on 2009-05-06
I'm not quite sure if /boot needs to be a primary partition, but to avoid trubble, I'd give it a primary one. If you go for encrypted /, /home, swap, etc., it's likely you'll run them as volumes and it doesn't matter which physical partitions build those those volumes.

---

