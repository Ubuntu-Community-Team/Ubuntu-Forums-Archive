---
title: "Can't login with X"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by LFS-Nr-3305 on 2009-11-01
Hi, 
I had a user, let it call "Nr1", in Ubuntu 9.04. Today, I made a distributions-upgrade to 9.10 "karmic koala". Since then, I can login as root, I can login as a new user created by root (let us call this one "Nr2"), I can do Strg+alt+1 and login as my old User "Nr1" in a terminal - but I can not login as my old user "Nr1" in "X" - the login screen would just flicker, show a fullscreen Terminal for a shurt moment and show again for login, or, if I chose a new login, fall back to what I was logged in previously, root or "Nr".

To work with my programs and data I had before, I either have to boot in "secure mode" or so (can't look it up as I am writing this from logged-in state, of course) or do a "sudo /etc/init.d/gdm stop" and in both cases, login and do a startx. 
I am not quite sure if it's a bug or a feature?! Please whoever has an idea why this happens, do not hesitate to enlighten me.

---

### Post by LFS-Nr-3305 on 2009-11-02
Has nobody an idea? I found out that on the bottom of the screen, I can chose if I wish to log into Gnome or KDE. If I chose KDE, I can login without any problem (but the upper part of the frame of any window is not visible, so I can't enlarge, close or iconify them - else I just would switch to KDE...).

So it is a problem with gnome and with the new boot system from Ubuntu, only.

I do not know what the following reactions do mean, either...?
---------------------------------------
gdm --version

** (gdm-binary:14414): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:14414): WARNING **: Could not acquire name; bailing out
root@junior:~# gdm --help
------------------------------------

---

