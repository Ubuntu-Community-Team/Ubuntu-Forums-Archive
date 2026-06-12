---
title: "What is Ubuntu doing?"
date: 2008-10-25
forum: General Help
---

### Post by Arukas on 2008-10-25
I'm playing OpenArena, in full screen.  The other day it did something weird.  The screen became a window on my desktop, All I was pressing asdw keys and the mouse button.  Anyone what caused this?  And how to remedy the problem install of having to crtl+alt+backspace?  

Also, this has happen with some other games, but I thought it was a game that didn't work.  OpenArena has never given me any problems before.


-Arukas

---

### Post by benny bronx on 2008-10-25
It may be the screensaver trying to activate. Go to system- preferences-screensaver and move the "regard the computer as idle after" button to a longer time.

---

### Post by ad_267 on 2008-10-25
This is a bug with Compiz, some people seem to think it's because the screensaver is trying to activate. See [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759).

You can disable Compiz to fix this, you could also try disabling the screensaver.

---

### Post by Arukas on 2008-10-25
I've read the thread.  But it does say how to fix the problem.  I don't know how to disable compiz, I can disable the screensaver.  How did a person goes into terminal to close a game when it didn't respond?

---

### Post by ad_267 on 2008-10-25
You can disable compiz by going to system - preferences - appearance - desktop effects and setting them to none.

You can go to a terminal by pressing Ctrl-Alt-F1 and then use "ps -e" to get the process id of the application and "kill ID_NO" to kill the process. You could also try "killall openarena" if openarena is the name of the application. Ctrl-Alt-F7 switches back to the graphical tty.

---

### Post by Arukas on 2008-10-25
when i press crtl+atl+f1, how do i get back to the gnome desktop?

-arukas

---

### Post by ad_267 on 2008-10-25
That's the Ctrl-Alt-F7 I mentioned.

---

### Post by buzzmandt on 2008-10-25
If you have access tp the terminal (i.e. the whole system isn't locked up) my favorite terminal command "xkill"
then point and click the window that's not responding and it's gone.

---

### Post by Shazaam on 2008-10-25
> **buzzmandt said:**
> If you have access tp the terminal (i.e. the whole system isn't locked up) my favorite terminal command "xkill"
then point and click the window that's not responding and it's gone.

You can also add that as a panel applet- right-click an empty space on the panel, go to "Add to panel", and look for "Force Quit" (same as xkill).

Arukas, open Synaptic and install "fusion-icon". This puts an icon in your panel that allows quick access for turning Compiz on or off if you need to to play games etc..

---

### Post by ju2wheels on 2008-10-25
Its no point, once it locks up like that even killing OpenArena doesnt help recover the mouse. You can successfully get to a tty term and back to the regular X session but the mouse will not be released. You will have to reboot, or at least that was the case every time it happened to me. Just disable the screen saver before you start playing. I play with compiz enabled all the time and it causes no problems.

---

### Post by Arukas on 2008-10-25
I turned the screen saver off, but I was still having problems.  Nothing since I disable compiz.  I hope that get it fix soon, that was a nice way to switch between desktops.

Thanks for all the help.

---

### Post by ad_267 on 2008-10-25
This might be useful: [http://ubuntuforums.org/showthread.php?t=867562](http://ubuntuforums.org/showthread.php?t=867562)

It lets you just switch to metacity while playing games. I was having the same problem so wrote this script.

---

