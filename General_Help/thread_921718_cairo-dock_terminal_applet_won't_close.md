---
title: "cairo-dock terminal applet won't close"
date: 2008-09-16
forum: General Help
---

### Post by uschxc on 2008-09-16
when i click the terminal applet from my cairo dock the terminal pops up but the X doesn't close the window and neither does ctrl+w.  but they both work on the 2nd, 3rd, nth tab.

any ideas?

---

### Post by stumbleUpon on 2008-09-17
Middle click closes the applet

---

### Post by bonzi on 2009-07-23
I dont use a mouse. Can I change the close function to left click?

---

### Post by fabounet on 2009-07-23
did you try to type "exit" ?
or just, to trigger the keyboard shortcut associated with this applet ?

---

### Post by ross.w on 2010-01-22
I have this problem as well. Trying any method to close the window merely moves it around the screen, apparently at random.

I have tried:
clicking the X
typing "exit"
clicking the middle mouse button on the icon
selecting "close current tab" from the icon's menu
pressing crtl-w
pressing Alt-F5

Nothing works except removing the icon altogether.

I am using Cairo Dock in 64 bit Karmic, with Compiz enabled on a Toshiba L500R with ATI Radeon graphics.

---

### Post by Saiko Berry on 2010-01-22
Find what the application is in system monitor.. gnome-system-monitor
Then type killall application name.

killall cairo-dock

---

### Post by boddhisatva on 2010-01-23
Same problem here on Karmic 64bit. The configuration window won't close, but the dock itself doesn't show like it used to on my previous system. I've had some strange behaviour from applications, but this is the weirdest.
@ Saiko Berry
It's not a question of just closing the application. I can just as well restart the system. It's a question why does it not work as it should and what can I do about it?

---

### Post by fabounet on 2010-01-24
consider upgrading the dock
it has been a reported bug some months ago, and is fixed.

---

### Post by Saiko Berry on 2010-01-24
or just dont use a dock. use quicklaunch programs like gnome-do or dmenu, i find they help you memorize your system much better anyways. docks decrease your knowledge of your own computer. icons in fact do.

---

### Post by boddhisatva on 2010-01-24
> **Saiko Berry said:**
> or just dont use a dock. use quicklaunch programs like gnome-do or dmenu, i find they help you memorize your system much better anyways. docks decrease your knowledge of your own computer. icons in fact do.

I remember my system all right - enough for my purposes anyway - and cairo-dock is a very convenient tool with LOTS of options to replace the rather cumbersome and old-fashioned way of getting to your applications and stuff. I've tried gnome-do and didn't like it.

[B]I got a (very fast) reply from the developers. I followed their advice and it worked!
Here's the link:[/B]
[http://cairo-dock.vef.fr/bg_topic.php?t=3904](http://cairo-dock.vef.fr/bg_topic.php?t=3904)

---

### Post by HaightsW on 2010-01-28
> I got a (very fast) reply from the developers. I followed their advice and it worked!
Here's the link:
[http://cairo-dock.vef.fr/bg_topic.php?t=3904](http://cairo-dock.vef.fr/bg_topic.php?t=3904)

Cheers for sharing this, it solved it for me.

---

### Post by tdeboeser on 2010-01-29
> I got a (very fast) reply from the developers. I followed their advice and it worked!
Here's the link:
[http://cairo-dock.vef.fr/bg_topic.php?t=3904](http://cairo-dock.vef.fr/bg_topic.php?t=3904)

Worked for me.  Thanks!

> **Saiko Berry said:**
> or just dont use a dock. use quicklaunch programs like gnome-do or dmenu, i find they help you memorize your system much better anyways. docks decrease your knowledge of your own computer. icons in fact do.

Ummm, not sure I understand this.  You have to put stuff you want in cairo-dock, thus you learn.  Plus this is a thread about the most powerful tool in any admin's box - the terminal.

docks increase your knowledge of your computer because you have to configure them - for your computer.  You'll put things in them that help you use your computer.  In fact the link above leads you to instructions, commandline instructions, to make your computer use the most resent version of this app.  And anything that doesn't work the way you need it to will lead you to learn about your computer...



Tom de

---

