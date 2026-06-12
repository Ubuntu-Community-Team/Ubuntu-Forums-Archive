---
title: "Problems booting/starting"
date: 2008-11-30
forum: General Help
---

### Post by Thesord on 2008-11-30
Recently I've been having some issues booting 8.04. Firstly, it hangs for a lot of time on the boot log (I guess that's what it can be called, I apologise for my ignorance) on the message:

Starting Common Unix Printing System: cupsd

Finally it reaches the login window stage. At this point, I type in my username and password and apparently log in fine, except for one thing. A window pops up with the following error:

"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or back.."

I did some research about it and found this page: [http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/](http://arunpc.com/2008/06/01/ubuntu-there-was-an-error-starting-the-gnome-settings-daemon/)

It seems this problem is related to configuring a wirelss connection through the GUI tool that come with Ubuntu Hardy as default. I use Ubuntu on my laptop mainly for programming uni projects and have it set to dual-boot with XP Pro 32b, though I'm considering using a single Linux OS on my laptop for everything (from programming to web surfing to gaming amongst others), so I'd be open to suggestions regarding that, although that'd be off-topic.

At the moment I can't configure Ubuntu to connect to my wireless home network (I know the connection details), which is unprotected just for the sake of testing... Furthermore, opening any application takes somewhere from 2 to 10 minutes. Plus several administration apps don't boot at all. I'm afraid I don't have much experience with Ubuntu so I'm kind of clueless as to what I should do to try and correct this problem. The last thing I did before this started happening was an attempt to connect to my wireless network through System -> Administration -> Network Tools and Network. I assumed there would be no chance of breaking my system through these interfaces (if "break" is indeed the correct term to apply here).

Help appreciated.

---

### Post by cmnorton on 2008-11-30
How much RAM is installed?

What kind of CPU do you have?

Can you use CUPS (print), once you boot?

Suggest you run top in an X-Term and monitor what happens when you start an application.

---

