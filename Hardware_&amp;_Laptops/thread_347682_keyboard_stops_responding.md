---
title: "keyboard stops responding"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by firstc624 on 2007-01-27
ok has anyone else had this happen?  your running your box just fine you leave for a while, screensaver or hibernate whatever comes on.  you return go to put your password in and the keyboard does not work..AT ALL

the mouse is fine, the power buttons all work, just he keyboard stops working.

Has anyoe found a way to fix this...because i have to hard shutdown my laptop to get things working again.

Thakns in advance

---

### Post by aidanr on 2007-01-27
i've had it happen all of twice, coming out of a full screen opengl app with beryl still running

[this]("http://en.wikipedia.org/wiki/Magic_SysRq_key") is the safer way of rebooting in that situation (alt+sysrq+s,u,b)

---

### Post by firstc624 on 2007-01-27
hot dog....

Now if i can just remember that


thanks a lot.  I really hated doing a hard shutoff but didnt' know any other way

This will work reguardless huh...even  though all keys seem to be locked out?

Thnaks

---

### Post by digital-IQ on 2007-01-30
I am having a similar issue with my Toshiba Satellite M35X-S311.  I have been running Dapper since July-06 with out any hardware issues.  Today if I leave my computer and let the screen saver start my keyboard will not respond.  I have to use my mouse to halt the screen saver.  I then have to click SYSTEM then QUIT and RESTART.  The machine fails to halt properly and I am left with holding the power button to shutdown.

Could this be a result of an updated packages that were installed yesterday?  I installed the following updates.

Upgraded the following packages:
acroread (7.0.1-0.0.ubuntu1) to 7.0.9-0.0.ubuntu0.6.06
automatix2 (1.1-2.8-6.06dapper_i386) to 1.1-2.9-6.06dapper_i386
firefox (1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
firefox-gnome-support (1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
libnspr4 (2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
libnss3 (2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06) to 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1
mozilla-acroread (7.0.1-0.0.ubuntu1) to 7.0.9-0.0.ubuntu0.6.06
wine (0.9.29~winehq0~ubuntu~6.06-1) to 0.9.30~winehq0~ubuntu~6.06-1

Installed the following packages:
acroread-escript (7.0.9-0.0.ubuntu0.6.06)

Any assistance would be appreciated.

Thanks

---

### Post by cossym on 2008-01-26
Exactly the same problem.  Screensaver comes on, halt screensaver with mouse, keyboard does not respond at all.  Caps/num lock keys do not change state or anything.

Started happening today (maybe yesterday at the earliest)

Any help on resolving this issue would be appreciated.

Scott

---

### Post by GuySmily on 2008-01-28
I started having this issue recently too, exactly as described above.  I don't think I made any changes before it started happening.

It used to only be an issue when the screensaver (set to blank screen) came on while I had a game running in WINE.  In fact I got scared because I typed in my password and hit enter at the login screen out of habit, then realized that it didn't get typed in the password box - I thought the game might have captured my keypresses, and I would have said my password out loud in-game (it's an online game).  I have since removed the password lock at the screensaver.

But now it will happen seemingly out of nowhere - though usually after I've been busy reading something or doing whatever without touching the keyboard (just mouse) for a while.

---

### Post by whitethorn on 2008-01-28
I have the same kind of problem.  I'm running Gutsy on a Dell Inspiron 8600, and sometimes for no reason that I've been able to figure out yet my keyboard just stops working.  The only button that actually does anything is the power button, when I press it it unmounts evrything and pretty much turn everything off and goes into a black screen and says Will Now Halt (doesn't do anything after that).  I then have to hold down the power key to turn it off for good.  My mouse works fine though, I've tried closing all the programs I had running but that didn't help bring my keyboard back.  I'd be really helpfull to get this fixed somehow.

---

### Post by GuySmily on 2008-02-01
Bump
Can someone lend us a hand?  I'm getting really sick of this issue, and I keep finding myself getting sick of restarting the computer all the time and just using Windows to get my job done.  Seriously the only reason I'm still booting into Ubuntu is my 30gb torrent is at 98% - yet lately my network connection has been dying too, regardless of wired or wireless it just drops me.  It seems like the keyboard fails at the same time, only the network usually comes back up after 30 seconds but the keyboard never recovers..  It still responds to SysRq commands though.

I am having NO issues with Windows btw

---

### Post by kseise on 2008-02-13
I have recently had a problem with the keyboard not responding after a period of inactivity.  I have tried two PS/2 keyboards and a USB wireless keyboard.  After a period of inactivity, Gutsy does not respond to the keyboard.  The mouse works fine.  With the wireless setup, the same USB plug connects the mouse and the keyboard.  The mouse works, the keyboard does not.  

This started happening after the updates on Monday February 11, 2008.  

As a work around, I have found that using the mouse to log out allows me to use the keyboard to log back in.  It seems to be a problem with GDM or possibly Compiz-Fusion.  I don't know enough to start hunting bugs, but if someone points me in the right direction, I would be happy to try.

---

### Post by lungdart on 2008-05-03
This issue started happening to me a few weeks ago. (end April 2008). I had recently installed deluge, AWN, and Compiz-fusion.

At first it would only happen while using deluge to download torrents, by which I now know, is a coincidence. This was with Ubuntu-7.10. Let it go to some weird configuration issue.

I formated and went with arch linux this time around (sorry guys :P), and all was fine until I installed the nvidia drivers and compiz fusion and awn.

A few hours later, keyboard froze. Mouse works fine, trying to shut down or log out through the menus does not work, the application just freezes. Alt+sysrq+b does not return my keyboard. Also any alt+sysrq do not seem to work all the time. (this could be just an Arch thing). Always required to restart.

After this had happened I killed all composite apps and switch to metacity using fusion-icon, but still no luck.

Who here who has reported this still has the problem and uses Compiz/Compiz-fusion/AWN etc?

---

### Post by crocowhile on 2008-05-06
Count one more here.
This is *so* annoying! I believe the bug might be related to gdm.
Please next time it happens to you pay attention the messages you get after you do a shutdown (using the mouse, of course): I get a segfault in gdm some kind of "error 4".
If we manage to narrow down this to gdm at least we know whose fault is it.

I am also a compiz user, with nvidia card (and one inactive integrated intel card). I have this problem only on a dell machine (not on the acer I have at home, despite running same stuff).

---

