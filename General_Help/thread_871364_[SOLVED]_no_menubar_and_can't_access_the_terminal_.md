---
title: "[SOLVED] no menubar and can't access the terminal in hardy"
date: 2008-07-26
forum: General Help
---

### Post by Benjaminp on 2008-07-26
I'm having exactly the same problem as hiro nakamatty ([http://ubuntuforums.org/showthread.php?t=828793](http://ubuntuforums.org/showthread.php?t=828793)) only it's a bit more complicated.
The reply to his post said:

Edit : did not see your last comment, Right click on your desktop & create a launcher for your terminal (above command) this may help you.

The problem is, when i right click on my desktop, nothing comes up... and Alt + F2 doesn't work..
I did set my desktop to be an animated matrix desktop, maybe that's why I get no results when I right click on the desktop.

Any help would be appreciated!

---

### Post by fooman on 2008-07-26
try this...press: ctrl-alt-f1

that should take you to a prompt. log in as root and type this:

```
apt-get install nautilus-open-terminal
```

hit enter and after it installs...reboot


when you get back to your desktop...right click and choose "open terminal"

type:

```
gnome-panel &
```

hit enter.

hope that helps.

---

### Post by Benjaminp on 2008-07-26
It installed, but still nothing happens when I right click on the desktop.

---

### Post by jimv on 2008-07-27
How did you set up your desktop to be animated?  Did you use the compiz or non-compiz method?  (as illustrated on this site:  [http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

---

### Post by Benjaminp on 2008-07-27
Actually I'm not sure :| Let me check on that:|
I definitely used the showdesktop = false, but I changed it to = true a couple days ago, and since then it hasn't been working.

Edit* Got it! I know that I used this code to show the screensaver (xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glmatrix -window-id WID), and stored that in "Sessions" in the ubuntu menu. I did have the showdesktop thingy in there too though.

Is it possible to edit the sessions list from the Ctrl+Alt+F1 terminal?

---

### Post by Zip247 on 2008-07-27
Did you happen to remove evolution from your machine recently?

---

### Post by Benjaminp on 2008-07-27
The evolution email client? Yeah I removed it about 2 weeks ago.
Should I reinstall it?

---

### Post by jimv on 2008-07-27
oops, double post

---

### Post by jimv on 2008-07-27
Try logging into the failsafe Gnome session.  THere should be a little button on the login screen that will let you choose which session you want.  Then you can undo the autostarting for your desktop background.

---

### Post by Zip247 on 2008-07-27
When you removed evolution you probably remove gnome-panel in the process.  Log into your ubuntu and clt+alt+F1 to get to terminal mode.  sudo apt-get install gnome-panel gnome-applets.  ctl+alt+F7 to go back to gdm.  You may have to restart x with ctl+alt+backspace.  Let us know if this fixes your problem.

---

### Post by Benjaminp on 2008-07-27
> **wdecker said:**
> When you removed evolution you probably remove gnome-panel in the process.  Log into your ubuntu and clt+alt+F1 to get to terminal mode.  sudo apt-get install gnome-panel gnome-applets.  ctl+alt+F7 to go back to gdm.  You may have to restart x with ctl+alt+backspace.  Let us know if this fixes your problem.

Nope, it says that it's already installed.

I'm posting from the failsafe gnome session. I'm going to go back to the original session... ill let you know how it works

---

### Post by Benjaminp on 2008-07-27
No luck.. I'm back in the Gnome Failsafe session... I tried removing the animated desktop scripts, then going to the normal session.. black screen, and nothing came up when I right clicked on the screen.
Went into the failsafe terminal mode... ran the gnome-panel & command.. the panel came up.. tried it in normal session after that... black screen and nothing coming up:P

---

### Post by Benjaminp on 2008-07-27
Got it!! i went into the failsafe gnome session, make a new session to run at startup (Preferences > Sessions) with the command "gnome-panel &" and that seems to have fixed it!
Only thing though... i don't seem to be able to right click on the desktop... in the gnome failsafe mode, or the regular mode.

Anyways thanks so much guys, I really appreciate your help!!

---

