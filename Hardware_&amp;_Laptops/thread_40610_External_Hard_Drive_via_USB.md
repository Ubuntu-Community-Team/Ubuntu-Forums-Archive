---
title: "External Hard Drive via USB"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by Nopposan on 2005-06-09
I just bought a Coolmax CD-310 external hard drive enclosure for the old hard drive on my wife's old computer; I'm trying to get it to work with Ubuntu but, of course, the CD-ROM it came with is made for Windows XP.

Can anyone help me get this thing configured so that I can read it?  I'm afraid I don't know how it's formatted, but it was running Windows 98.  The problem is that I don't get anything in the "Computer" window in Gnome for the hard drive.  I think it's showing up as a USB connection on the Gnome device manager though.

---

### Post by tristan on 2005-06-09
Hmm, Ubuntu usually does a pretty good job of automounting USB drives, whether they be flash or HD. It shouldn't matter what filesystem the external drive has on it (probably Fat16 or Fat32 if from Windows), gnome should just mount it as **40Gb media** - or whatever size it is.

Do you have a flash drive too? If so, does it show up when you plug it in?

If none of your USB drives show up, it means there's something a bit wrong with the automounting (which has been documented here before). You might be able to give gnome a little bit of a push to make it detect them. The way I do it is just type **killall gnome-volume-manager** in a terminal. Then reset your computer and your drives should show up.

If other USB drives show up but not your HD one, then I'm not sure what the best course of action is. There are plenty of experts on these forums who should be able to help!

---

### Post by Nopposan on 2005-06-30
I formatted the external HD as NTFS, but the Ubuntu Linux laptop reads it just fine.  Thanks, Tristan.

---

