---
title: "OS wont boot after installation!"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by 2002maniac on 2009-02-11
I think I fuxxored a Ubuntu install on my new(Dell refurb) laptop. I managed to complete the partition of the hard drive (50/50 for windows and ubutu) and set up the OS but now when I boot up without the ubuntu image CD, it goes straight to XP with no option to boot linux.

So now my computer is way slow and the hard drive is half the size. Is there any way to undo the partition and delete all things ubuntu from outside of the OS? I don't have a XP boot CD.

Any help would be appreciated.

Thank you!

---

### Post by k3rnelmustard on 2009-02-11
so, you got the lappy from dell, did you shrink windows and install ubuntu in the rest of the space or did you wipe the existing os, and install ubuntu and windows from scratch.  If so, which order did you install in?

I guess most importantly, do you want help fixing the dual-boot or help wiping ubuntu more?  If you want to wipe ubuntu it's easy.  Boot up the ubuntu livecd, open gparted, delete the ubuntu partition, and then grow the windows partition to eat up all the newly-free space.

---

### Post by 2002maniac on 2009-02-12
Xp was already installed.  I rebooted with the Ubuntu CD in the drive and chose to do a dual boot install.  I'd like to get it to work if I could, but I might just have to wipe ubuntu and stick with windows for now.

I'll try making the changes in Gparted like you say.

---

### Post by boywander on 2009-02-12
You could try to install again or just drop it for now.

I got the same issue with Gutsy/Intrepid, and believe it was just something screwy about the way the installation set up grub. The howto sorted me out.
[URL="http://ubuntuforums.org/showthread.php?t=224351"]http://ubuntuforums.org/showthread.php?t=224351
[/URL]After following I also needed to edit /boot/grub/menu.lst in the Ubuntu install, to point it to the correct partition for XP.

---

