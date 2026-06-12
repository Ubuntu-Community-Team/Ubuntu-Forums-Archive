---
title: "upgrade boot menu"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by wallywally on 2009-05-23
My wife's Sony Vaio has been running Vista and Hardy side by side quite happily for some time until I decided to install Jaunty on top of the Hardy space (note not upgrade) yesterday.  The install seems to have been successful except for the fact that the boot menu is still giving the option for loading 8.04 and 9.04 is nowhere to be seen.

Is it possible to remedy this from the livecd or do I need to fiddle around with vista?

---

### Post by lindsay7 on 2009-05-23
Try alt + f2 then enter update-manager -d and see if you get anymore updates.

You can also try typing sudo gedit /boot/grub/menu.lst and post the results here. That will show what is in you grub menu and what is listed.

---

### Post by wallywally on 2009-05-26
> **lindsay7 said:**
> Try alt + f2 then enter update-manager -d and see if you get anymore updates.

You can also try typing sudo gedit /boot/grub/menu.lst and post the results here. That will show what is in you grub menu and what is listed.

Cheers for that lindsay and apologies for my tardiness in replying.  It didn't help in itself but whilst hunting down my grub menu I found (remembered) that I had Easy BCD running in Vista.

Easy BCD is an excellent piece of kit and I can't recommend it enough.  The only problem comes when the nitwit user forgets that he is using it :(

See - [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Cheese!

---

