---
title: "Keyboard layout switching shortcut doesn't work UNTIL I hit Properties."
date: 2008-10-14
forum: General Help
---

### Post by vicky molokh on 2008-10-14
Greetings, all! 

I'm having a problem with my keyboard layout switching. I use Ubuntu, and recently updated to the Hardy (initially installed from the Gibbon CD), but I don't think the upgrade's the reason. Here's how it works, and how it doesn't:

Upon startup and login, the key combination for layout switching doesn't do anything (I use left Alt+Shift). If I left-click on the Keyboard Indicator, it switches, but the combination DOESN'T stop working. So I go right-click on the Keyboard Indicator, click Keyboard Preferences, Layouts, Layout Options, and Close. After that the switching combination starts working.

Rebooting makes it stop working again, but restarting X using Ctrl+Alt+Backspace does no harm. 

I tried looking at Sessions to check the running stuff (with the intent of putting xkb or whatever it is into startup programs), but there's no difference between running stuff before and after I go to the Layout Options. 

I still suspect it's some service or daemon or program that doesn't start until I fiddle with Options, but I have no idea how to pinpoint it. 

Any advice? 

Thanks in advance!

---

### Post by vicky molokh on 2008-10-16
BTW, what's strange: the layout options do *not* show a line at the bottom of the window.

Back when I had Mandrake/KDE, there was a line indicating the options chose, similar to command-line parameters.

---

### Post by vicky molokh on 2008-10-17
Found a weird solution:
add setxkbmap (without any parameters) to the Session Startup Programs. For some reason, now it works (and now it displays in the currently running list).

Also, as strange fact: on a new user, xkb seems to work perfectly. However, after changing some of the settings it stops starting automatically as it's supposed to. What gives?

---

