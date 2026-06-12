---
title: "Toshiba A500 Nvidia driver causes  white screen."
date: 2010-08-04
forum: Hardware
---

### Post by pave_spectre on 2010-08-04
Finally got sick of windows 7 so decided to install ubuntu on my toshiba satellite A500/01K laptop, as a way of getting back into linux. (ex slackware desktop user many moons ago).

So far having 2 issues. graphics (GeForce® GT 230M) and bluetooth. Bluetooth I am not really worried about as I hardly ever use it.

Graphics on the other hand is beginning to irritate me.

I cannot for the life of me get the nvidia driver to work properly, and so far have tried 3 different driver versions with the same end result, a screen covered by lots of white lines, to the point where the screen is almost completely white.

Haven't got a pic of my screen but if you look at this guys screen,

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160643&d=1276700678[/IMG]

where he has that bar across the middle, that is what my entire screen looks like.

I know it is still booting up as I can perform the login blind, and hear the logins sounds going on.

Have not been able to find anything that helps so far, and would appreciate some assistance.

currently running 9.10, but had the mostly the same problem in 10.04 (except the last time where it stopped booting entirely)

---

### Post by pave_spectre on 2010-08-07
Anybody?

---

### Post by pania on 2010-08-07
I have GeForce GT 230M and had similar problems and installed the nVidia driver version 256.44 and now my system is fine.

Read this

 [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

and if you install that ppa and then update your system with all the updates you should be fine. I would also update normally before installing that ppa.

---

### Post by pave_spectre on 2010-08-14
Didn't work unfortunately.

tried installing that ppa, and updating, but installing the nividia driver results in the same white screen.

---

### Post by pave_spectre on 2010-08-14
And to top it off I now appear to have broken a number of the System --> Preferences programs, keyboard, Monitors, Mouse etc.
gives errors like -- "failed to execute child process "gnome-mouse-properties" (no such file or directory)"

--EDIT--

Ok fixed all those. Now it's just the nvidia driver giving me trouble still

---

### Post by pave_spectre on 2010-08-20
bump

---

### Post by pave_spectre on 2010-08-24
Nobody?

---

