---
title: "Starting again with a fresh install"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by blaise69 on 2009-10-19
Hello everyone,

I'm a fairly experienced #! (and Ubuntu) user and due to all sorts of reasons wich I won't bother going into here, I would like to freshly install my operating system.

My current version is #! 8.10, and I have it installed on one of 3 partitions I have on my HD, this partition apart from having the OS install also holds all my media and work and other documents, the other 2 partitions are for Windows 7 (games) and then the swap partition.

**My question begins here**, I would like to install the latest version of #!, but I don't want to lose any of my work or other files in my Home Folder, and I also want to change the size of this partition slightly.

Can anyone recommend the best process for this? I'm under the impression that if I install #! form a Live CD, it will wipe everything I have there at the moment, I find copying and replacing my Home folder using an external HD time consuming and fairly inelegant.

Is it recommended to create a new partition solely for my Home folder?   Will this hook up into the OS seamlessly when I upgrade in the future?

With new linux builds coming out every 6 months on average, I find I often want to upgrade my OS, and I still haven't worked out the best way to manage my files.

Any tips and advice for the perfect Linux setup would be greatly appreciated.

Cheers,

Blaise.

---

### Post by earthpigg on 2009-10-19
always back up your home prior to anything involving partitions, fresh installs, or upgrades. ***period.***

not that that's done:

during the 'manually partition' phase, if you pick your current /home partition during the install and set it's mount point to /home and 'do not partition', then theoretically it will remain intact.

if you do NOT have a /home partition currently and want to set one up in conjunction with a fresh install:

-back up your /home.
-do the above.
-move the backed up /home over to your new /home partition.

---

### Post by MelDJ on 2009-10-19
if you install ubuntu with wubi, keep your songs, pictures, etc, in host. that makes it a lot safer in case ubuntu crashes, your files will be safe.

---

