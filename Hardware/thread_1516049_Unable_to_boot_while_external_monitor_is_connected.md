---
title: "Unable to boot while external monitor is connected"
date: 2010-06-23
forum: Hardware
---

### Post by NanakiXIII on 2010-06-23
Up until today, I was able to use an external monitor with my laptop as a second screen without too many issues (though Ubuntu isn't very fond of it). Today, however, Ubuntu suddenly wouldn't boot anymore. I'm assuming it was booting out of view, but there was no display on either my laptop monitor or the external monitor. If I disconnect the monitor, everything works fine.

This is a specific Linux problem, it seems. It affects Ubuntu, Ubuntu's installation CD (not just the Live distribution, nothing on the CD is accessible, including the installation procedure) and also an old Knoppix Live CD I have lying around. My Windows XP installation works just fine with the external monitor.

It was not the only problem I had today and though I do not see quite how myself, I suppose the problems might be correlated. What happened earlier today was that
- I got an update notification from the update manager. When I clicked install, however, it would pop up a progress bar, doing something, but dropped this process after a few seconds and returned to the update list. Nothing got installed.
- I was trying to install OpenSSH and I had to edit a configuration file. When I tried saving my changes, using GEdit, it kept throwing a segmentation fault.
- After the above problem, I tried restarting the laptop. When it booted back up, Ubuntu would not allow me to log in. It simply did not load up the login dialog, or any of the panels you get to choose which desktop environment you want, etc. I tried logging in from the command line, but it would not accept my login information. This may have had something to do with the fact that I created a user sshd, which the program wanted.
- I booted back and forth a few times between Windows and Ubuntu, googling on XP and trying stuff on Ubuntu. I booted into recovery mode at some point, but could not find anything that seemed useful to me. I then tried booting the Ubuntu Live CD so I could back stuff up and wipe the installation, at which point the current problem started occurring.

I have now managed to reinstall Ubuntu, but the problem with the external monitor persists. Can anyone think of a reason why it suddenly stopped working?

---

