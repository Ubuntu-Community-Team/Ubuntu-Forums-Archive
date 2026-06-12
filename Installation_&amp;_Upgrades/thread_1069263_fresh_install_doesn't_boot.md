---
title: "fresh install doesn't boot"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by th00ht on 2009-02-13
On my Shuttle Xf61b I attached a second HD to install Ubuntu 8.10. First of all I wanted to leave alone the WinXP disk but it did't. Without me asking it installed grub on that and I have to somehow get rid of it, because... Ubuntu does not start on the second disk:

Boot from (hd1,0) ext
Startup up...
[...] Kernel panic - not syncing: VFS: Unable to mount fs on unkonwn-block(0,0)

So two questions:
1) how do I restore the original WinXP partitions on the first disk?
2) why isn't ubuntu starting?

---

### Post by Pumalite on 2009-02-13
You can fix your Windows MBR with your Installation Disk:
Hit 'r' for Recovery>FIXBOOT>FIXMBR
Or Super Grub

---

### Post by Taemojitsu on 2009-02-13
it didn't actually touch your windows partition, it changed the MBR which used to point at your windows partition and now points at grub.

I made the mistake of installing grub onto windows partition because I thought it would store files there :&#8203;( (This meant when I tried to start windows, it ran Grub from my linux partition instead... which listed Windows, which actually ran grub.. which listed windows....)

(alright so I guess it changed your windows DISK, but not your windows PARTITION...)

Grub should load when you select the windows disk to boot from?? -confused-

Or, did you correctly format the Ubuntu drive when you installed?

---

