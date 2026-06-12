---
title: "Using windows xp and kubuntu on 2 HD?"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by encompass on 2006-01-23
The site should be back up now... they had some server problems
did you have the drives and switch them and now your installing ubuntu?  if so... I don't think you should have to many problems. otherwise... you will want to reinstall grub.  Search these forums for that answer... and then post the link to your solution on your thread here.  Hope that helps.

---

### Post by shafer5 on 2006-01-23
I was just wondering what i have to do in order to run windows xp on my primary slave drive? heres what i got did:

> installed kubuntu on my master drive
unplugged the master HD
plugged in the other HD as a master HD and installed XP on it
set the jumpers on the xp HD to primary slave
set the jumpers on the kubuntu HD to master


now is there any settings i have to change?


also....whats been up with this site? i have been having trouble getting it to come up the last few days?

---

### Post by makisupa123 on 2006-01-25
[QUOTE=shafer5]I was just wondering what i have to do in order to run windows xp on my primary slave drive? heres what i got did:



now is there any settings i have to change?


also....whats been up with this site? i have been having trouble getting it to come up the last few days?[/QUOTE]

I have a similiar setup.  Breezy on my main HD and XP on a slave.  This is the relevant portion of my /boot/grub/menu.lst that gets XP to boot.  Essentially, you are tricking it into thinking that its the first drive:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



title Windows XP
map (hd0) (hd1)      # Tell the first hard drive to pretend to be the second
map (hd1) (hd0)      # Tell the second hard drive to pretend to be the first
root (hd1,0)         # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (hd1,0) # GRUB won't attempt to mount the Windows drive
makeactive           # Sets the partition to active
chainloader +1       # Tells GRUB to load the Windows bootloader when done

---

