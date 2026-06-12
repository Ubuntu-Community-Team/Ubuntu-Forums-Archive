---
title: "I would like to remove 9.04 off my computer"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Halcyon31415 on 2009-06-21
I installed Ubuntu 9.04 and would like to remove it. I enjoy 8.04 much more and would like to either move 8.04 to the top of my Grub boot options so i can start to computer hop in the shower and come out and have my prefered distribution running. 

Could someone please help me either move 8.04 to the top of Grub or show me what files I would need to remove and where they could be located on my HD.

I hope removing 9.04 will involve learning some new commands in the Terminal. I love typing things in the terminal makes me feel like I'm really doing something cool! :)

Thank you

---

### Post by Mark Phelps on 2009-06-21
If you "upgraded" from 8.04 to 9.04, there is no simple way to "remove" 9.04 because you're really asking for a rollback.  The only way to go "back" to 9.04 is to reinstall from scratch.

The 8.04 kernel is still in your boot list because you did an upgrade.  But that upgrade installed a lot more than just a new kernel.  So, while you could change the menu.lst default selection to point to 8.04, you'd still be running the other newer packages, just an older kernel.

---

### Post by raymondh on 2009-06-21
Hello halcyon31415,

Mark Phelps is right.  Unless you have 2 versions in your HD now (8.04 and 9.04, each in its' own partition) you are looking at a clean, re-install of 8.04.

If you do have 2 versions, you can always delete what version you don't like and extend the size of the remaining.  These links are refernce materials just in case you do delete and resize.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

You may have to re-edit your menu.lst (or re-install GRUB) depending on how you have it configured prior to any deletion. But, we can go from there depending on what you decide to do.

Good luck.

---

### Post by Halcyon31415 on 2009-07-04
I went for the reformat, it seemed like the easiest approach in the end. I got a western digital passport and spent about an hour backing things up and re-installing. Man I forgot how much better Ubuntu is at installing then windows. If I want to put XP on my computer it is something like 4 reboots for all the drivers that Ubuntu finds on it's own. Man I love me some Ubuntu :)

---

### Post by raymondh on 2009-07-04
Congratulations and happy Ubuntu-ing.

---

