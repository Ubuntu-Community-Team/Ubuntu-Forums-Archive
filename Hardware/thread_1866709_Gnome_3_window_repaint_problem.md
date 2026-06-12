---
title: "Gnome 3 window repaint problem"
date: 2011-10-21
forum: Hardware
---

### Post by wiscalico on 2011-10-21
Hi.

I just wondered if anyone else is experiencing that Gnome 3 (gnome-shell) sometimes doesn't repaint window content. I'm running Ubuntu 11.10 and installed Gnome 3 instead of Unity. When I run Gnome in fallback mode this doesn't happen.

I have experienced this in gnome-terminal (exiting vim, running ls -l) and Emacs (pressing page down or selecting text). But by pressing Ctrl + Alt + left arrow (or right) or pressing print screen I can force the window to be redrawn.

I tried both the proprietary Nvidia driver in Ubuntu 11.10 and the driver proprietary available through X-swat team PPA (currently running version 285.05.09). Also sometimes X seems to increase in cpu usage after a while (constantly using around 10-20%) and this significantly increases the frequency of the "bug".

This also happened in 11.04 running Gnome 3 from the PPA.

I can't seem to find a bug report about it in launchpad. Does anyone else experince this?


This is the closest I get to other people experiencing the same problem:
[http://www.motifzone.net/forum/incomplete-redraw-text-widget-under-gnome-3](http://www.motifzone.net/forum/incomplete-redraw-text-widget-under-gnome-3)
[https://bbs.archlinux.org/viewtopic.php?id=119884](https://bbs.archlinux.org/viewtopic.php?id=119884)

---

### Post by Ozzee on 2011-10-25
I have the same problem. No idea how to fix it tho. :/

---

### Post by wiscalico on 2011-10-25
What hardware do you have?

Mine is a Dell Latitude E6400

---

### Post by davidbarton on 2011-11-08
I have the same problem intermittently on a Dell XPS 1530.  

Thunderbird and Chrome suffer more often than most.  For example, a change happens within a page in Chrome and it doesn't redraw until I run the mouse over it.  Selecting messages in Thunderbird doesn't display them in the message pane.

It may be related, but I have a noticeable lag (1 - 3 seconds) when switching tabs in Terminal.  I eventually switched to Terminator to allow multiple shells on one tab, but tab switching within Terminator is also slow (but not as slow as Terminal).

Unity is also very buggy for me, otherwise I'd use that :(

---

### Post by wiscalico on 2011-11-09
Usually I can get the lag to stop for a short while by restarting gnome-shell (Alt+F2: r)

What Graphic card does your Dell XPS 1530 have?

---

### Post by davidbarton on 2011-11-09
> **wiscalico said:**
> Usually I can get the lag to stop for a short while by restarting gnome-shell (Alt+F2: r)

What Graphic card does your Dell XPS 1530 have?

Thanks, wisacalo.  Restarting does fix the problem for a very short time.  After some small use (in one case, just opening the Activities window list) it slows down again.

I have an nVidia GeForce 8600M GT with the driver "version current".

For anyone else who tries alt-f2 + r and their shell gets stuck, run gnome-shell --replace

---

### Post by davidbarton on 2011-11-14
Another strange thing.  Switching from one workspace to another sometimes takes 15 seconds or so while the computer just sits there doing nothing.  This is especially likely if the workspace is empty.

---

### Post by davidbarton on 2011-11-29
I finally switched to xubuntu as my default desktop.  WOW!  It is fast.  There are a few niggles compared to gnome, but I've fixed nearly all of them.

The exact same apps run much faster e.g. Terminator so it might be the graphics library or something.

FWIW, after a few days getting used to it, I really liked Gnome 3 except for ALT-Tab showing windows on all workspaces.  However xubuntu is just so much faster I can't give that speed up.  I'll check up again in 12.04

---

### Post by sebpop on 2011-12-29
Hi,

Updating to 11.10 with Unity, I also am seeing the repaint problems on Xterms and Emacs.
When pressing Ctrl-L in both a terminal or in emacs the windows get repainted sometimes
correctly, sometimes in a different way with other parts of the window text missing.
To reproduce the repaint problem I force repainting with Ctrl-L: this sometimes gets the
content of a window incomplete.

My laptop is a Lenovo X120e with an AMD E-350 Processor
VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
I do not use the proprietary graphics driver.

---

### Post by bobbaluba on 2012-02-12
Did you ever find a solution? I have the same problem on an iMac.
The bug is most frequent when i use texmaker, but also in gnome-terminal.

---

### Post by wiscalico on 2012-02-13
No haven't found a solution...

The real problem is that I have no idea what is causing this.

Right now I'm just living with it :(


If I ever find the time I'll try install another distro like Fedora...
perhaps it is caused by a specific patch that Ubuntu applies.

Does any know if this has been reported as a bug?

---

### Post by bobbaluba on 2012-02-22
> **wiscalico said:**
> No haven't found a solution...

The real problem is that I have no idea what is causing this.

Right now I'm just living with it :(


If I ever find the time I'll try install another distro like Fedora...
perhaps it is caused by a specific patch that Ubuntu applies.

Does any know if this has been reported as a bug?
After a bit of searching, this is what i found:
[http://forums.fedoraforum.org/showthread.php?t=274021]("http://forums.fedoraforum.org/showthread.php?t=274021")
[https://bugs.launchpad.net/ubuntu/+source/vte/+bug/809911]("https://bugs.launchpad.net/ubuntu/+source/vte/+bug/809911")
[https://bugzilla.gnome.org/show_bug.cgi?id=657994]("https://bugzilla.gnome.org/show_bug.cgi?id=657994")

With one exception (earlier in this thread), this seems like an issue related to the nvidia proprietary driver.

EDIT: and this [https://bugzilla.gnome.org/show_bug.cgi?id=657071]("https://bugzilla.gnome.org/show_bug.cgi?id=657071")

---

### Post by wiscalico on 2012-10-01
I found this bug report today which might be related: [https://bugzilla.gnome.org/show_bug.cgi?id=664858](https://bugzilla.gnome.org/show_bug.cgi?id=664858)

---

