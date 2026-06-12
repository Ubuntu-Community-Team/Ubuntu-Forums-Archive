---
title: "[SOLVED] Grub menu from flash drive"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by nickski on 2008-12-14
Okay, i have recently installed hardy on a 4 gig flash drive.  I must have not been thinking clearly, because now, i cannot boot up my computer without that flash drive, because the grub menu is now loaded with hardy.  I have 2 other os's on my actual sata hd, which are vista and intrepid.  Is there any way i can go back to the old intrepid boot menu?  I'm afraid i will lose my flash drive and not be able to boot into any of my other os's.  Any help will be greaaaatly appreciated.

---

### Post by nickski on 2008-12-14
never mind, i have figured it out.  I went into terminal and used sudo grub, then at first i had read a tutorial that said to put in root (hd0,0).  I did that with no luck.  But when i went into menu.lst i saw that my 8.10 partition was actually (hd0,4).  After i learned that, i was successfully able to change it.  Hope this helps anyone who has had my problem.  this thread helped me....[http://ubuntuforums.org/showthread.php?t=558720](http://ubuntuforums.org/showthread.php?t=558720)

---

