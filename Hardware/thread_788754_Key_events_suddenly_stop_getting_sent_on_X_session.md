---
title: "Key events suddenly stop getting sent on X session"
date: 2008-05-10
forum: Hardware
---

### Post by dsmith4 on 2008-05-10
Distribution: Ubuntu Hardy Heron (Upgraded from Gutsy)
Desktop Environment: KDE 3.5.9

My keyboard seems to randomly stop working in an X session.  I was able to use Ctrl-Alt-F1 to use the console, and the keyboard works there.  I was also able to start a new session, and the keyboard works in that session while at the same time it doesn't work in the previous session if I leave it open.

When this happens I also notice that when I click on menus with the mouse on applications written for gnome (GTK), the menu doesn't react to clicking on it with the mouse, however it does highlight when I move the mouse over the menu item.

xev shows mouse events, but not keyboard events in the X session with the problems.

When I open the Hardware Testing utility, a message box pops up saying "Could not grab your keyboard."

I am leaving the X session with the problem open for now since I want to figure out the cause of this problem, and I don't know how to cause.

This problem wasn't occurring in Ubuntu Gutsy.

---

