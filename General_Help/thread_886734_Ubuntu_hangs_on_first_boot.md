---
title: "Ubuntu hangs on first boot"
date: 2008-08-11
forum: General Help
---

### Post by Delta62 on 2008-08-11
I have recently installed Ubuntu onto ym laptop. Using the desktop and alternate CDs did not work, so I eventually used the mini ISO and successfully installed. The only option I chose to install other than the base system files was the ubuntu desktop. Installation completed succesfully, with no errors.


However, now there is a new problem. I have noticed the same symptoms when booting from the desktop CDs to try Ubuntu without making any changes. Before the OS completes loading, the following text comes onscreen:

*starting anac(h)ronistic cron anacron [OK]
*starting deferred execution scheduler atd [OK]
*Starting periodic command scheduler crond [OK]
*Checking battery state [OK]
*Running local boot scripts (/etc/rc.local) [OK]
_


The underscore there is a blinking cursor. Needless to say something is preventing Ubuntu from loading right. Th screen will stay like this until the computer is restarted.

What can I do do get Ubuntu up and running?

---

### Post by cariboo on 2008-08-11
What are the specs of your laptop? What cpu, how much ram? If you are not sure, hit Ctrl-Alt-F2 this will open up another console with a login prompt. Login using the user name and password and entered during setup, when you are logged in type:

```
startx
```

It looks like the gnome desktop manager didn't get installed. Typing the above command should get you a desktop.

Jim

---

### Post by Delta62 on 2008-08-11
I've got an AMD athlon XP XPU at 1.7GHz, and 512 MB RAM. Onboard video, LAN and a mini PCI wireless G card.

ctrl alt F2 does bring up a text based login screen. after entering my username and password, I typed in the startx command. Here's what happened:

X.org X Server 1.4.0.90
Release Date: 5 sept 2007
[....]
Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up
xinit: connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.

---

### Post by Delta62 on 2008-08-11
Could this be an issue with my video card being incompatible with the operating system?

---

### Post by Delta62 on 2008-08-17
I have now also tried running fluxbuntu.

This OS will run fine, witha graphic interface. However, fluxbuntu is not as user friendly as Iwould like.

Anyone have an idea what's going on here?

---

