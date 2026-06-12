---
title: "[SOLVED] session lasted less than 10 seconds......error"
date: 2008-10-23
forum: General Help
---

### Post by aaron1011 on 2008-10-23
got a problem

upon trying to login to ubuntu 8.04 LTS, after typing my username and password the sysstem boots and this window pops up that says:

Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

Details:

/etc/gdm/Xsession: Beginning session setup...
bash: /usr/share/reconstructor/scripts/boot-scripts-exec.sh:
Setting IM through im-switch for locale=en_US.
Start Im through /etc/X11/sinit/xinput.d/all_ALL linked to /
**Message: Another GPG agent already running

SESSION_MANAGER=local/aaron-linux:tmp.ICE-unix/7215
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

(gnome-settings-daemon:7239): Gnome-WARNING **: error caching sample <-1>!

Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present.

---

### Post by x1a4 on 2008-10-23
Hi,
Log in to a Failsafe Terminal session, wait 15 seconds, log out, than log in again normally.

---

### Post by aaron1011 on 2008-10-29
logged into failsafe terminal, waited 15 seconds, typed quit, then logged in like normal and the problem is still there.

please help!   i have several files in ubuntu i would not like to loose!!

as soon as i click (ok) on this window, ubuntu restarts.

---

### Post by neighborlee on 2008-10-29
> **aaron1011 said:**
> logged into failsafe terminal, waited 15 seconds, typed quit, then logged in like normal and the problem is still there.

please help!   i have several files in ubuntu i would not like to loose!!

as soon as i click (ok) on this window, ubuntu restarts.

GO into failsafe mode,,and  start checking around to verify problems, like the noted disk full.

NO need to panic just yet .

cheers
nl

---

### Post by aaron1011 on 2008-10-29
I can go to failsafe mode, but i have no idea where to start or what to do once i get there.  how do i check if my disk is full?
and if it isn't what other problems should i look for?

---

### Post by aaron1011 on 2008-10-29
resolved.........

my splash screen was causing the problem.   after i disabled the splash screen on startup the problem no longer occured.

---

### Post by snova on 2008-10-29
Which one was it? It may be a bug the developers would like to know about.

---

### Post by red_team316 on 2008-11-01
> **snova said:**
> Which one was it? It may be a bug the developers would like to know about.

It's most likely not a bug but user error. He remastered ubuntu with [reconstructor](www.reconstructor.aperantis.com). Since the problem was supposedly the usplash, it's most likely that he replaced it with a corrupt usplash downloaded from somewhere, accidentally installed a 64-bit usplash instead of a 32-bit one or vice versa, or (most likely) attempted to create a usplash with reconstructor(which has been broken since edgy and is noted in reconstructors readme file. Please use [TUM 1.04](http://forumubuntusoftware.info/viewtopic.php?f=23&t=1767&sid=dee60fd1ccd026d34d5a345b63444270) or latest version of TUM to create usplashes instead. There are no plans to fix reconstructors usplash code, but rather usplash creation will be handled through TUM in future releases of reconstructor.)

You can also look at the /usr/share/reconstructor/scripts/boot-scripts-exec.sh script to also get a better idea of what other customizations were made to the CD. I typically install whatever software I need into the LiveCD rather than having it run on boot.

---

