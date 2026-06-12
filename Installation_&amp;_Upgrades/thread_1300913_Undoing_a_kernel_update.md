---
title: "Undoing a kernel update?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by nevarDeath on 2009-10-25
So the other day I got an update notification for a newer kernel and some libpopp stuff for pdf rendering. I dutifully upgraded and upon restart, my wireless wouldn't work! the kernel was upgraded to 2.6.28-16-generic I am using ubuntu 9.04. So I switched from madwifi drivers to ath5k and that worked fine, but I need the madwifi drivers for packet injection. When I switched back to madwifi, wireless quit working. I goggled around and found out about hitting 'esc' at the grub menu and selecting a previous kernel 2.6.28-15-generic and everything was fine again.

So I edited /boot/grub/menu.lst and changed the default number to 2 so it will always boot the 2.6.28-15-generic kernel.

Everything is fine, but I am wondering if it's safe to continue to apply updates as normal or upgrade to ubuntu 9.10 in a few days? Can i just pretend like nothing happened or do I need to undo the kernel 2.6.28-16-generic upgrade somehow? I'm not updating anything till I can find out more about this, thanks in advance!

---

### Post by nevarDeath on 2009-10-29
So does anyone have an opinion on this? I hate to try the 9.10 update with this config issue....

---

