---
title: "Resume from suspend driver problem"
date: 2011-04-16
forum: Hardware
---

### Post by acornbrain on 2011-04-16
I am using Ubuntu 10.04 on an older Dell laptop c610 with an ATI radeon M6 LY video driver. 

Everything works fine, but the display will never resume after suspend/hibernate/lid close.

I feel like I have read a thousand forum posts similar to mine, nothing every seems to do the trick.

Has anyone had any success with this card?

---

### Post by acornbrain on 2011-04-17
HELP PLEASE
 
I went and followed the instructions at this site:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
 
after "simulating" the suspend, the laptop display failed to wake (like I knew it would), I did a hard shutdown and restated. but now I can't log in properly...
 
first I get this message on the screen at boot:
 
init:hwclock main process (XXX*) terminated with status 1
 
(*this number is different every time)
 
and when I finally log on, all of my panel applications (indicator aplet, trash, etc) won't load. In System Monitor, it shows all of their processes as "sleeping"
 
HOW DO I WAKE MY COMPUTER BACK UP?
 
-brian

---

### Post by acornbrain on 2011-04-20
OK, I "solved" the problem. While I was in the BIOS, I noticed that the clock was set to the wrong time and the year 2048! After I fixed that, everything more or less booted up normally.

I am still having some lingering problems. I can't get my network manager applet to show in the notification manager automaticaly, I have to launch it manually.

Also, I can't edit my network connections anymore. Used to be, it would just ask me for the administrator password, but now it just says "insufficient privelleges" and won't let me.

Plus, I can't install programs through the software center. It used to ask me for the password, but now I just hit the "install" button and nothing happens.

Seems like something went blooey with my user permissions. If I start noticing more annoying stuff like this and I can't fix it, I'm going to start over with a clean install.

-brian

---

