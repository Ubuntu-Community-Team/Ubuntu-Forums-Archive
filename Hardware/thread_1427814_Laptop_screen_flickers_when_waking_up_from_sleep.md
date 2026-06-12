---
title: "Laptop screen flickers when waking up from sleep"
date: 2010-03-12
forum: Hardware
---

### Post by kcee08 on 2010-03-12
Hi

I've been experiencing flickering when the system wakes up from a sleep mode(or screen saver mode).  The screen goes really garbled and I've been powering off the system to reboot.  I'd like to stabilize my laptop so that I can really migrate to linux.

_Here is my system:_
os: Ubuntu 9.10
laptop model: Acer Aspire 5100

I'm not sure whether this is all I need for you guys to diagnose the problem.

Thanks and I hope to hear from you.

Regards,
Kevin

---

### Post by crlang13 on 2010-03-12
Hey.  I had a similar problem on my MSI.

I take it you're duel booting?  What version of Windows are you using and do you have a similar problem there?

---

### Post by kcee08 on 2010-03-13
I'm using windows vista and that surely works.  Why? Are you experiencing flicker problem on your windows?

I think I've asnwered your question already but yes i'm using dual os.(win vista and ubuntu 9.10)

---

### Post by crlang13 on 2010-03-13
I'm not using Windows.  I did have Windows XP on my MSI but got rid of it.

On Ubuntu 9.10, I got a flickering screen as well.  I looked into it on the MSI website and they said there was a bios problem on Windows 7 and had a download to fix it.  I saw in my research that that bios update would work on ubuntu 9.10.  I don't know why, but there is something similar in the way Windows 7 and Ubuntu 9.10 works and the bios update will help both.

I took a look on the acer website for you.  Unfortunately, there is no bios for Windows 7 for your particular model... Is it an older model?

I don't know enough about the exact little bits of the operating system so I don't know what's changed in Windows 7 and Ubuntu 9.10 that's causing these little problems, but have you tried Ubuntu 9.04?  You may have to use that until Acer decides to update it's bios.

** Keep in mind that's just my interpretation of the problem based on my experience with a different model of computer.  Either way, goodluck with the problem :p

---

### Post by emoritz on 2010-03-15
I have the exact problem. I'm running Ubuntu 9.10 / Windows 7 on an Acer Aspire 5100. The screen flicker only occurs when attempting to resume from suspend/sleep/hibernate in Ubuntu, while Windows works perfectly.

Based on some reading the problem appears twofold:
Xorg has a bug in it. It remains unfixed.
ATi no longer supports Linux drivers for these "older" models.

The best option I've seen so far is to disable all power saving features, ie. suspend/sleep set to "Never", "Do nothing" on close lid, uncheck "Monitor power control" and basically don't use suspend/sleep.

It's unfortunate and definitely suboptimal but it seems that the only way to not get screen flicker on resume is to not go to sleep in the first place.

---

### Post by pennypecker on 2011-01-09
Hello!
I have the same problem with Ubuntu 10.10: after resuming from screen saver (or without screen saver after resuming from display sleep) the screen flickers for a period of time. 
[LIST]
I've noticed that if the screen was sleeping or in screen saver for a long time, it takes longer to function correctly without flickering. 
[/LIST]
[LIST]
I have a Fujtsu Siemens Esprimo Mobile V5535, with SiS 771/671 graphic card
[/LIST]
[LIST]
The reslution is set to 1280x800, and refresh rate to 60 Hz
[/LIST]

The work-around was to disable screen saver and never put monitor to sleep. 
Any ideas about how can this damage (or not) the monitor? The first time I experienced this was after a period of 1h minimum of screensaver running. I shut down the laptop, and after 10 minutes booted, entered the bios, and even there it was flickering. So I suppose this could damage the monitor, and it's not happening only in Ubuntu.
Thanks alot!

---

