---
title: "[SOLVED] Lost Gnome start panel! Help!"
date: 2008-07-16
forum: General Help
---

### Post by quixote on 2008-07-16
I can't even get at the terminal and try to use command line because there's no way to get at the menu item to launch it.

Using Ctrl-alt-F1 is no solution because then I have *only* a terminal, and can't try to fix the GUI desktop.  (For instance running gnome-panel or gconf-editor says it's not installed. . . .)

[This bug]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg922604.html") seems related, and it refers to [this forum post]("http://ubuntuforums.org/showthread.php?t=705269") where it says the problem is "fixed."

I don't see how.  It says the problem is a setting in compiz and to turn that off.  But how can I turn off any settings if I don't have a GUI or terminal way to get at the preferences??

---

### Post by Cone on 2008-07-16
Try hitting Alt+F2 and typing ```
metacity --replace
``` and see if that gets your stuff to show up again.

---

### Post by Joe of loath on 2008-07-16
try the command gdm or, if that doesnt work, xdm. that should bring up the GUI as normal.

---

### Post by quixote on 2008-07-16
Neither suggestion seems to work.  :(

I've tried them from a terminal via ctrl-alt-F1, and then restarted the system.  I also tried them after booting into recovery mode at the root prompt.

gdm gives the same screen with no start menu.  xdm is said to be not installed. (both run as sudo)  (I think xdm *is* installed.)

Metacity --replace says "windows manager error.  Unable to open X display".

In recovery mode as root, I tried startx then, but it just brought the same no-start-menu window back, plus a message about a problem with HAL, probably because it hadn't gone through the whole boot process before that.

Am I missing a step?

---

### Post by knutschr on 2008-07-16
When you have loaded to Ubuntu:
[Alt][F2]
```
gnome-panel
```

I also experienced the disappearance of panels yesterday after last update.
I had to make it like i wanted again, but now it is OK.

---

### Post by quixote on 2008-07-16
I found another thread with this exact problem and the solution:  [[SOLVED] gnome panel both gone - hardy 8.04]("http://ubuntuforums.org/showthread.php?p=4988910")

That user had the issue just after uninstalling evolution and . . . the user I was trying to help had just uninstalled evolution.

Accepting the default dependencies to uninstall results in gnome-panel being tossed out. 

 :KS Hello?  Developers?  This is a Very Dumb Default!  Fix it *pronto*, PLEASE!  (Evolution, unlike Thunderbird, doesn't have the option for multiple email accounts.  For some of us, that's a showstopper.  It takes up lots of space & has constant updates.  So there are plenty of people who'd like to remove it.  If they aren't careful about **not** accepting the default removal of dependent packages, they'll be dead in the water, just like this user was.  Erm, what ARE you thinking??)

So, anyway, /*end blowing off steam*/ the solution is to boot into recovery mode, get the root prompt, enter ```
apt-get install gnome-panel
```, type exit to get back to the four boot choices, and proceed with "normal boot."

If it complains about missing applets, start synaptic, and install gnome-applets if it is no longer installed (which was the case for us).

---

### Post by quixote on 2008-07-16
(Looks like knutschr is on the same wavelength at the same time :)  )

---

### Post by joexs on 2008-07-17
SO glad I found this post.  I happened to install a new video card at the same time I uninstalled Evolution (and of course accepted the defaults), and lost the panel bar.  I spent a couple of hours just KNOWING it was the video card that did it.

Many thanks!!

---

