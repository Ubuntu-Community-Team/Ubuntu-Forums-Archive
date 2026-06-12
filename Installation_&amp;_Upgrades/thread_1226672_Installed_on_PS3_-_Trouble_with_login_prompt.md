---
title: "Installed on PS3 - Trouble with login prompt"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by fatpenguin on 2009-07-29
Hello - 

I have installed the Xubuntu 9.04 PPC PS3 build onto my PS3, and it boots into the window manager and gives me the login prompt in the lower left hand corner.  The mouse is responsive, as is the keyboard.  If I attempt a bad login, it tells me I have an incorrect user/pass combination.  However, when I input the user/password I setup on installation, the system turns grey on the password input block, and stops.  The mouse remains responsive, but it does not do anything, and does not login.

Has anyone seen this issue?  Any suggestions (or anyone know of the best version of Ubuntu to use with a CECH model PS3)?  I forget the command to exit out of the X-windows login and get to another shell prompt.  I would like to simply see if I can get into a command line prompt.

Thanks for any help you can provide,
Adam

---

### Post by fatpenguin on 2009-07-29
I have attempted to install ubuntu as well, in case it was an issue with the window manager, but I have the same result.  Any thoughts?  It's supposed to go straight to a desktop after logging in, correct?

I have access to the shell from kboot, is there any sort of setup I can change through that console to help me out with this?

---

### Post by fatpenguin on 2009-08-05
I am able to get to a terminal by pressing CTRL-ALT F1, and back to the GUI with CTRL-ALT F7.  I am able to login to a command line, and I seem to have full administrative access.

Can someone point me to the command line to launch xwindows from a terminal when logged in (so that it does not require the user to login to a GUI?)  I still have the issue where the GUI login locks up when entering the username/password :(

Also, X seems to be running with the following arguments:
/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

Is there anything obviously wrong with this, that could be causing the login to lock up?

There's also a couple of programs running under my username called /usr/bin/aplay (with the argument of a wav file), /bin/sh /usr/lib/gdmplay /usr/share/sounds/question.wav, and /usr/bin/gnome-keyring-daemon --damonize --login.  Could the login for ubuntu lock up if it is unable to play sound on the PS3?  Can I disable the playing of any sound until I get the sound drivers working?  I'm thinking this could be an issue, and will be my next place to look unless anyone has more feedback...

Thanks!

---

