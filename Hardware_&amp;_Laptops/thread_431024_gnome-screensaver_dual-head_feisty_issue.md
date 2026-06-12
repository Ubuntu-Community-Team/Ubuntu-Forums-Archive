---
title: "gnome-screensaver dual-head feisty issue"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by whistl on 2007-05-02
I have a laptop with external LCD display attached, running a dual-head display config on Ubuntu 7.04 Feisty Fawn.  That part is working fine.  The annoying issue I'm running into now is that the gnome-screensaver idle timeout only pays attention to keyboard/mouse activity on screen 0.

Since my external display (screen 1) has more real estate (1920x1200) I tend to use it more often, but every 15 minutes the screensaver kicks in and I am forced to move my mouse pointer over to the laptop screen (screen 0), just to "wake up" the screen saver.

This behavior didn't occur under Ubuntu 6.10 (Edgy Eft), it only started after I upgraded to the latest version.  Any ideas?

---

### Post by Eddie Hung on 2007-05-13
I can confirm I see this issue too - I have a dual head setup on a desktop, and I have to move the mouse back onto the primary screen periodically to prevent the screensaver from thinking I'm idle, and launching itself.

Quite annoying, I must say!

I can only confirm this in Feisty - as I didn't have a dual monitor set up when I used Edgy.

Eddie

EDIT: I've checked launchpad and there doesn't appear to be a bug filed about this under "gnome-screensaver" (is this the right package?) - should we file a new one? [https://bugs.launchpad.net/gnome-screensaver/+bugs](https://bugs.launchpad.net/gnome-screensaver/+bugs)

---

