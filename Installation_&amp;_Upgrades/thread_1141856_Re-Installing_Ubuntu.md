---
title: "Re-Installing Ubuntu"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by arepaking on 2009-04-28
Hello Experts,

I want to do a Jaunty fresh install in my computer. My current system structures goes like this:

a) One partition has Windows XP (Primary)
b) One partition has Ubuntu (Extended)

What should I do in order to erase Ubuntu and install a new fresh version? what about the current GRUB settings? 

Thanks in advance for your guidance,
AK

---

### Post by oldos2er on 2009-04-28
Boot the Jaunty LiveCD, when the installer runs the partitioner, choose 'Manual" and point it to your current Ubuntu installation. Your Grub should be automatically updated.

---

### Post by taygan on 2009-04-28
> **oldos2er said:**
> Boot the Jaunty LiveCD, when the installer runs the partitioner, choose 'Manual" and point it to your current Ubuntu installation. Your Grub should be automatically updated.

I did the manual partition editor, selected the partition I'd been using as '/' and I DIDN'T format the partition.  This way all my home folders are still there (I do rename my /home/username folder to /home/username-old so I don't overwrite it.)  I've had a few issues with hidden kernels left over, and there may be other stuff, so it's not a fully clean installation, I suppose it's not much more work to just backup and restore the home folder..  ah well.

Don't worry about your windows partition on the partition editor.  It will not be "used" (nor will swap).  Ubuntu will find the existing swap and windows partitions on it's own.

---

