---
title: "Why does 9.10 upgrade want to remove xscreensaver?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by bpeyser on 2009-10-31
Just got the upgrade notice today (64-bit desktop) and it says:

**Not all updates can be installed**
blah, blah, blah...

So I can choose to run a partial upgrade. If I click "Partial Upgrade" I get a notice asking if I want to start the upgrade, saying that 2 packages are going to be removed, 4 new packages are to be installed, and 7 packages are to be upgraded. The installed/upgraded packages all have to do with R (a statistical scripting package), one of the packages to be removed is r-base-latex, and the other to be removed is xscreensaver. I could lose r-base-latex and not get it back, and it would be fine.

But, why does the upgrade want to remove xscreensaver, and will it install a new version of it? I REFUSE to upgrade if I have to use gnome-screensaver, and may consider going to another distro. I generally like gnome and ubuntu, but gnome-screensaver is a bridge too far with the interface nazis. Unless there's someone new in charge of gnome-screensaver who is willing to make it actually function.

Does xscreensaver work with 9.10? And does anyone know if I should do a partial upgrade and/or why it's necessary? I have repositories for R, Medibuntu, and archive.canonical.com/ubuntu jaunty partner listed in third-party software. Do I need to change the third-party sources to karmic instead of jaunty? And should I uncheck the third-party sources until after upgrade? I'm going to wait to upgrade for now, but want to do it soon.

Thanks!

---

### Post by bpeyser on 2009-11-02
Well I went ahead and took the plunge after making an image of my partition.

Yes, the upgrade process removed xscreensaver and installed gnome-screensaver. And yes, the same interface nazi is still running the show. Removing gnome-screensaver and adding xscreensaver from within Synaptic package manager was no problem, and xscreensaver remembered all my settings.

So far, so good. Too bad the upgrade process insisted on gnome-screensaver, but the fix was pretty easy. Just nuke gnome-screensaver and install a real screensaver and what do you know? I can actually configure my screensavers again! :o

-bpeyser

---

### Post by eulu on 2012-04-13
still doing this in 12.04 too..

---

### Post by bpeyser on 2012-04-13
Meh, it's only been broken for 3 years. :rolleyes:

Of course, I didn't actually submit a bug until a year ago:

[https://bugs.launchpad.net/update-manager/+bug/775369](https://bugs.launchpad.net/update-manager/+bug/775369)

Not as bad as gnome-screensaver, which has been broken for almost seven (7) years! That's like 49 in non-computer industry years. :lol:

---

### Post by oldos2er on 2012-04-13
Closed, necromancy. Please don't bump old threads.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

