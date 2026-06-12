---
title: "Taskbar missing after updating driver?"
date: 2011-07-10
forum: Hardware
---

### Post by Smokexz on 2011-07-10
I have a laptop with an Nvdia Geforce GTX 260m, and when I installed an update for a "restricted driver" I started up Ubuntu to find that neither the bottom or top bars are there. I am extremely new at this and have been a Windows user for all my life, this is very new to me. So after this driver being installed(I installed the one it recommended, to stay on the safe side) it just doesn't work, I can still access stuff through the file browser and stuff but I need these bars. Oh I was also trying to add some effects to my desktop using this application called Compizconfig or something like that.


Please and thank you!

---

### Post by Smokexz on 2011-07-10
Is there really no one who can help?

---

### Post by charliewhizbeez on 2011-07-10
It could very well be compiz.  A similar thing happened when I tried to use unity after using classic.  Try doing a gnome reset.

I'm not sure, but try typing 

Gnome -- reset in terminal

Or metacity --reset.

ctrl-alt-f1 takes you to a terminal session
Ctrl-alt f7 to exit.
Here is the link to the forum that helped me:

[http://ubuntuforums.org/showthread.php?t=1772605](http://ubuntuforums.org/showthread.php?t=1772605)

Dont forget to restart x!

---

### Post by milgner on 2011-07-21
I had this problem on a lot of machines now.
Removing the metacity package always helped, seems like Unity doesn't really like it...

---

