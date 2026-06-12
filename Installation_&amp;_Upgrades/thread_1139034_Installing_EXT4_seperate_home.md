---
title: "Installing EXT4 seperate /home"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by LIB53 on 2009-04-26
I'm in Ubuntu 9.04 RC liveCD mode. Can anyone tell me how to install a separate home partition on my external FreeAgent Drive? My setup right now is a 80GB internal with WinXP 63.86GB and then a 1.33GB swap and a 9.33 EXT4 with jaunty on it. I'm deleting this install though (messed up drivers). And then I have a 250GB FreeAgent drive (external HDD) that's all NTFS. What I want this to be is 10GB Jaunty ext4 on my 80GB HDD with winXP untouched, and a 20GB "/home" on my FreeAgent drive with the existing NTFS partition still their with all my data.

I also want to know if this is even a good idea. I don't know if this a stupid thing to do. If it's not a bad option, where would you recommend i put my swap partition?

---

### Post by LIB53 on 2009-04-27
Nvm, I solved it. I just made a ext4 partition on my 80GB internal, and then another on my 250GB external. When i installed Ubuntu, i chose manual partitioning, and edited the ext4 partition on my 80GB drive to have the mount point as "/" and then changed the mount point on my 250GB disk to "/home". I still want to know if this slows the system or anything. I am kind of seeing a Ubuntu crash a bit, but that might just be coincidence.

---

### Post by jsonder on 2009-04-27
> **LIB53 said:**
> Nvm, I solved it. I just made a ext4 partition on my 80GB internal, and then another on my 250GB external. When i installed Ubuntu, i chose manual partitioning, and edited the ext4 partition on my 80GB drive to have the mount point as "/" and then changed the mount point on my 250GB disk to "/home". I still want to know if this slows the system or anything. I am kind of seeing a Ubuntu crash a bit, but that might just be coincidence.

I had an ext4 partition for the os (9.04betaNR) and an ext2 for /home on a Dellmini9.  No problems, but to ensure that there wasn't polling/tracking I reinstalled the os on ext2, with a straight 9.04beta ext2 installed in between.

Is the external drive powered up before you boot Ubuntu?  I suspect that it must be "ready" to be seen during the boot.

---

### Post by LIB53 on 2009-04-27
Everything is working, it just seemed a bit crash happy at first. I would be customizing something and it would go blank and send me to the login screen. It's running fine as of right now though.  Might crash any second however, i haven't had that much time with it. My external drive is one those Seagate externals that use USB, so it is powered on when i boot. I'm just curious as to whether this method has any problems or limits on the system stability and so forth.

 And what do you mean by polling/tracking? Excuse me for being noob.

---

