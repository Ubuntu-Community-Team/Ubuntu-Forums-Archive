---
title: "Create dual boot from existing patitions"
date: 2008-10-02
forum: General Help
---

### Post by sdlyr8 on 2008-10-02
So I've been using Ubuntu happily for 2+ years now. When my new job says I will need to use Windows for some of the things for work. Not a big deal... Used GParted to shrink my ubuntu partition and put a 40 gig partition with XP Pro on it. Now I reboot and don't have a boot menu to choose from. How do I create a boot menu to let me choose which OS i want to start in?

Thanks!

---

### Post by mikewhatever on 2008-10-02
Grub boot loader needs to be recovered.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by /////// on 2008-10-02
After recovering the grub bootloader which was covered by mikewhatever, you may also have to add the xp partition into your GRUB menu. To do this simply edit the grub menu file by opening a terminal and typing "gksu gedit /boot/grub/menu.lst" without the quotes. After this, add the windows partition in after the linux boot options at the bottom. To add the windows partition just type this:
title           Windows XP
rootnoverify    (hd0,1)
makeactive
chainloader     +1
where hd0=first hard disk and the 1 represents the second partition if thats how you have ti set up. If it isn't, just adjust accordingly

---

### Post by sdlyr8 on 2008-10-02
Thanks guys! That's what I needed!

---

### Post by Sand Lee on 2008-10-02
Don't forget to mark this thread as [solved].
You can do this through, Thread Tools -> Mark thread as solved

---

