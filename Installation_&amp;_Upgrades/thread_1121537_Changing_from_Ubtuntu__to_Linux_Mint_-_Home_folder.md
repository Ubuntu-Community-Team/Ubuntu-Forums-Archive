---
title: "Changing from Ubtuntu  to Linux Mint - Home folder"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by ravenus on 2009-04-10
I am thinking of changing over to Linux Mint...no specific reason, just feel like trying it out.
My Home directory is located on a separate partition. If I install Mint, will it be able to access the current Home directory or will it have to be created afresh?

Thanks for any advice.

---

### Post by coffeecat on 2009-04-10
In theory there's no particular problem with sharing a home partition, or using an old one. Since Mint uses the same UID (1000) for the first user, you won't even get any permissions problems. The Mint installer is the same as the Ubuntu installer, so you can choose 'Manual' at the partitioning stage and tell the installer to use your home partition for /home and not to format it.

However, I can foresee one big problem. Your home folder contains a number of hidden configuration files for applications and, more importantly, the gnome desktop. Mint has a very individual way of tweaking gnome - that's part of the attraction of Mint. It's possible - but I can't be sure - that by using your Ubuntu home folder, your Mint desktop will look like Ubuntu, or be some peculiar hybrid - orangey-mint perhaps? :wink:

As I said, I can't be sure. I've never tried it! :) I'm just raising a possible problem. All I can say is, give it a try. The worst that happen is that you'll have to re-install. Just back-up any valuable data and personal files first.

Good luck, and tell us how you get on.

---

### Post by ravenus on 2009-04-11
@coffeecat:

Thanks a lot for the very helpful reply. It'll probably be a small while before I install, since I'm getting busier at work and I feel this is the sort of thing that deserves a weekend, just in case things don't go hunky dory ;) But when I do, I'll be sure to share my experience.

---

