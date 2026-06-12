---
title: "will there be any negative effects if I interupt a distro upgrade?"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by joshuapbell on 2009-03-13
I want to interupt it and wait till I get my laptop home due to the slow Internet speed here at work? good idea? bad idea? no idea?

---

### Post by cyran on 2009-03-13
If the slow internet is the problem, it sounds like you're still downloading all the packages. Interrupting the upgrade while it's *still downloading* is harmless; the changes it's done already will be reversed. Once the downloading is finished, then you can't interrupt it (that's what the warning says, anyway).

---

### Post by joshuapbell on 2009-03-13
> **cyran said:**
> If the slow internet is the problem, it sounds like you're still downloading all the packages. Interrupting the upgrade while it's *still downloading* is harmless; the changes it's done already will be reversed. Once the downloading is finished, then you can't interrupt it (that's what the warning says, anyway).

Cool thanks

---

### Post by carml on 2009-03-13
> **cyran said:**
> If the slow internet is the problem, it sounds like you're still downloading all the packages. Interrupting the upgrade while it's *still downloading* is harmless; the changes it's done already will be reversed. Once the downloading is finished, then you can't interrupt it (that's what the warning says, anyway).
+1, I suggest you to wait until it finishes,if you can.

---

### Post by afrodeity on 2009-03-13
well, I just had one hell of a two day upgrade in which my computer partially upgraded, aborted and then resumed. I am now happily over the bumps and appear to have Intrepid. Linux headers for 2.6.22-24.49 are downloading and not sure if this is part of the general install or because I could have the wrong repos, but generally my faith is restored. Was expecting to have to install off a CD and wipe my partition, but this is not the case. So, it could be fail-safe install if interrupted, but no guarantees. Just faith that one can get out of install/upgrade hell if you perservere, have some good company, drink a beer and let the machine do its thing.

---

### Post by punong_bisyonaryo on 2011-04-30
I wasn't too sure if I should create a new thread, but this thread seemed appropriate.

I did a distro upgrade to Natty, and when I left the house the downloading was just about done. However, the power went out after an hour or two, apparently, interrupting the upgrade.

Now when the computer starts, it fails to mount / (seems it doesn't know how to)

Is there a way I can backtrack or resume the installation from where it was interrupted? Is it even possible to determine where it got interrupted?

Thanks!

---

### Post by afrodeity on 2011-04-30
Usually what happens if the installation was interrupted during the downloading of the packages, the downloading will just resume with **update-manager -d**, however it appears there is either a hardware issue (check to see if harddrive is actually connected) or some file corruption, in which case you need to **fsck**. Check this thread [http://ubuntuforums.org/showthread.php?t=1305434](http://ubuntuforums.org/showthread.php?t=1305434)

---

### Post by dino99 on 2011-04-30
maybe recovery mode then "repair packages"

but always for installation/upgrading, deactivate: screensaver, suspend/hibernate, well everything that can disturb

---

### Post by punong_bisyonaryo on 2011-05-01
Hi thanks for the replies!
But they didn't work for me, I didn't have a GUI, just a terminal shell. And it was definitely not a hard disk problem (at least not hardware-wise).

After figuring out how to fix the mounting of my drives (editing grub boot options, changing fstab, manual mounting /home), I just did a 

dkpg --configure -a
apt-get dist-upgrade

Got that idea here: [Recover from shutdown during Ubuntu distribution upgrade]("http://serverfault.com/questions/8540/recover-from-shutdown-during-ubuntu-distribution-upgrade")

---

