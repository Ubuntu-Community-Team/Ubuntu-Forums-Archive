---
title: "Failure of second kernel 2.6.27-11 installlation"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by leopards on 2009-01-30
After second update to kernel 2.6.27-11 today I get error 11: Unrecognized device string  Had to boot with 2.6.27-9 to get online to ask for help! Already did a re-install, didn't help!

---

### Post by cocopuffz on 2009-01-30
Same problem for me. Im booting from .9
.11  cant find the right hdd.

---

### Post by leopards on 2009-01-30
At least you know it is the HDD that it can't find! I had no idea what the problem was! Todays first update to 2.6.27-11 went fine, the second one caught me by surprise, then on reboot an error message!

---

### Post by tommcd on 2009-01-30
Try the solution posted in post #6 of this thread. It worked for at least one person.
[http://ubuntuforums.org/showthread.php?t=1053203](http://ubuntuforums.org/showthread.php?t=1053203)

---

### Post by leopards on 2009-01-30
Didn't help! got an error can't find pkg!

---

### Post by leopards on 2009-01-30
Problem solved! After reading some of the posts on similar problems checked QGRUBEditor and noticed the was no entry for root for the 2.627-11 kernel! Fired up nautilus and checked the menu.lst and saw that ther was no hda,0 after root!!! Added that to the lines for the generic and recovery versions of 2.6.27-11 rebooted and everything worked fine! Major clue was the first person that posted that it didn't find the hard drive!!

---

