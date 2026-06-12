---
title: "Gnome Menu bar/Task bar on wrong screen (Dual-screen setup)"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by GMU_ninja on 2009-11-08
Hello,

I recently upgraded from 9.04 to 9.10.  The system worker without flaw with 9.04 and it seems to work fine with 9.10 with one exception.  The menu bar and task bar have switched screens, and this is very annoying.

I have a dual screen setup (side by side) with the left screen as the "primary" screen (a Samsung SyncMaster 225BW) and the right screen as the "secondary" screen (a NEC MultiSync LCD1760V).

What I am calling the menu bar (the bar at the top that contains the Applications, Places, System menus; the shortcut buttons; the date/time, and "system tray" without a better name) and the task bar (the bar at the bottom with the show desktop button, and the buttons for all my open windows) used to be on the primary screen in 9.04, and after the upgrade to 9.10, they moved to the secondary screen.

How can I move these two bars to the primary screen again?

---

### Post by ermejo on 2009-11-18
I had the same problem.

I solved it by:

- click on the top bar with the right mouse button, somewhere where there are no icons. Select "Properties". Deselect "Expand".

- on the left of the bar, you now will have a handle. Click and drag the handle to the screen where you want the bar.

- done.

---

### Post by audiomick on 2009-11-18
That worked for me too. I had to mess around a bit, as my screens are very different sizes. I seem to remember re-expanding after I had it where I wanted it.

Just checked; with expand de-selected, it is a short bar, when it is expanded, it fills the width of the screen it is on.

---

### Post by pvledoux on 2010-03-11
Same problem here. I have a laptop, and when I connect the 2nd screen, the toolbar goes on that screen.

My work around is to disable the second screen, close the NVidia config window, reopen the config window, re-enable the second screen, et voila, the toolbar don't moved.

Strange bug, I was wondering if I was alone ;)

Maybe I will post a bug report.

[EDIT]
bug reported here: [https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/537177](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/537177)

---

### Post by Cloggsy on 2010-03-11
I regularly project from Jaunty on a laptop and it's taken me a while to sort this. In the Nvidia control panel click on "X Server Display Configuration" where the laptop screen and the projector (or second screen) are shown side by side. The projector is enabled by configuring the screens as "Twin View". There is a check box to tick which is the "primary" screen - i.e. the one with the toolbars. In my experience it is invariably the "wrong" one which initially shows the toolbars but I've discovered that if I disable the second screen for a moment and then re-enable it with exactly the same settings then the toolbars are on the correct screen.

---

