---
title: "Theme Disappears"
date: 2008-11-22
forum: General Help
---

### Post by Unanimated on 2008-11-22
Yeah, okay, sometimes when I'm using my computer, my theme will suddenly disappear and be replaced with a default, bland, and ugly thing. Here's a screenshot of it happening while I'm running the DarkRoom theme. I don't know how to get it back, but messing with the Appearance preferences seems to work, but I would prefer it never happens to begin with. It isn't just the Darkroom theme that it happens to - it's happened to Human and other themes before, as well.

Yes, that's my Last.FM profile.

EDIT: I just got an error message saying "unable to start gnome-settings-daemon." It said some more stuff, but I can't be sure of the specifics.

---

### Post by Yellow Onion on 2009-01-15
have you tried resetting the theme in system> preferences > appearance
because I'm having the same problem and if i try opening "appearance" X crashes
Perhaps you should report this bug on Lauchpad?

---

### Post by itchanddino on 2009-01-18
I have the same problem.  What I do is open the Appearance menu and it resets to Human.  But why does this happen almost every boot?  It only started for me after I enabled then disabled compiz effects.

---

### Post by UBB2 on 2009-02-26
I have that problem, too, it's funny that it does not happen always when I log in, just about half of the logins. I have a fully customized appearance with a new pointer, window border etc., the only thing that gets lost is my Glider theme, everything else is normal.

---

### Post by smani on 2009-02-26
I think it is a bug in the gnome-settings-daemon which crashes. After the theme has changed, you can try to run gnome-settings-daemon from terminal. In my case the X server crashes. It could be related to the bug I have filed here: [https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/318684](https://bugs.launchpad.net/ubuntu/+source/seahorse-plugins/+bug/318684)

---

### Post by melikamp on 2011-07-28
I have a similar problem with 11.04 and Gnome 2.32.1. I use classic login and compiz. My theme of choice is Human. Sometimes right after login (feels like exactly every other time) compiz loads with an ugly black theme, then quickly resets to an ugly default theme. I log out, log in again, and lo, Human is back. Very annoying, but not a show-stopper. I tried erasing all related settings from the graphical recovery console:

```
rm -r .gnome2  .gnome2_private .gconf .gconfd .compiz .config
```

The bug persists.

---

