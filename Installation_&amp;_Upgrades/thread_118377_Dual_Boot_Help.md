---
title: "Dual Boot Help"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by WoodPost on 2006-01-16
Here what happened, i went t install 5.10 on my computer, and it worked fine, even with a software raid setup. My problem was that when you booted the PC it defaulted to Ubuntu instead of Xp which is also installed. That did not bother me but it would have bothered my parents, who are weened on Xp. So i went to uninstall it, and somehow messed up GRUB. When i did that i couldn't get XP to boot anymore, so instead of using my Live CD to get to the Internet and look for a solution, which i should have done in hindsight, i reinstalled windows, bad idea, now my parents are pissed. My question is that is there a way so XP is the default OS during boot and won't need to be chosen or have to hit any keys or anything, i just want to turn the computer on and have it boot into XP. If i want it to boot into 5.10, i can choose or or something, thats what  need help with.

---

### Post by Sef on 2006-01-16
How to change the grub:

> Actually, are you asking what you need to change to have Windows XP as the default boot system? If so, you don't need to add anything, just change as shown here in bold:

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 5

Your default wait time before the system automatically boots into the default is currently set at 10 seconds. You can reduce that somewhat, but be careful not to make it too short. If you make it 0 or 1 second, then you won't have time to change the boot to Ubuntu when you want to.

To read the full post:  [http://ubuntuforums.org/showthread.php?t=112632&highlight=set+grub+default]("http://ubuntuforums.org/showthread.php?t=112632&highlight=set+grub+default")

---

### Post by WoodPost on 2006-01-16
What file do i modify, and where would i find it?

---

### Post by jjross on 2006-01-16
Try checking out this link, it is what I use and it works really sweet and it is not that hard to do. Good luck
Bye the way,  if I could do this ,anyone should be able to.


[http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)

---

### Post by Sef on 2006-01-16
Here's a post that explains how to go into and change the grub:

> It's actually not very difficult, but you may need to experiment a little.

in a terminal type, "sudo gedit /boot/grub/menu.lst" without the quotes, of course.

(I suggest you make a backup before doing this, just in case.)

Scroll to the bottom of the file, you'll see the entry(s) for your Linux partition(s).

Right under that add these lines.


title Windows 95/98/NT/2000 (make this whatever you want it to say)
rootnoverify (hd0,0) 
makeactive
chainloader +1

Now here's the trick, where it says, "root (hd0,0)" you'll have to figure out what drive and partition your Windows partition is

Link to post: [http://ubuntuforums.org/showthread.php?t=116093&highlight=grub+set]("http://ubuntuforums.org/showthread.php?t=116093&highlight=grub+set")

---

