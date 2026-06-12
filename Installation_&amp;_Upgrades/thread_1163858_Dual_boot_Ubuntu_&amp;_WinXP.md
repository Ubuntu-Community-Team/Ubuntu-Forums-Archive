---
title: "Dual boot Ubuntu &amp; WinXP"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by David C. on 2009-05-19
I've spent the better part of the day wrangling w/Windows XP & Ubuntu 8.10. I installed Ubuntu first, then XP. Of course, XP didn't recognize the linux partition among other issues (like not recognizing the entire 500GB SATA HDD, but that's another issue). Any way, I managed, thru the use of a tut, to get back into Ubuntu and do some fixes.

I did the following to get the GRUB config working via the Live CD, entering the following in the terminal:

root (hd0,0)
setup (hd0)
quit

Rebooted w/out the Live CD and entered: sudo gedit /boot/grub/menu.list

Add the following at the end of the file, below ###END DEBIAN AUTOMATIC KERNELS LIST

title     Windows XP
root      (hd0,1)
makeactive
chainloader +1

I also added # to hiddenmenu so that I could have the GRUB menu always avail & increased my timeout to 15secs.

I rebooted again, grub menu came up, with Windows XP at the bottom of the list, I selected it and got this:

Invalid device request

Any ideas?

---

### Post by finito on 2009-05-19
[http://ubuntuforums.org/showthread.php?t=1163503](http://ubuntuforums.org/showthread.php?t=1163503)

---

