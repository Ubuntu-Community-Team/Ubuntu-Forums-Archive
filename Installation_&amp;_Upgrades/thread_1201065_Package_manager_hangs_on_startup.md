---
title: "Package manager hangs on startup"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by SuperCave on 2009-06-30
I have been using Xubuntu for about 7 months on an Eee pc 900 from an SD card.I recently installed Skype from a downloaded package; I'm not sue if that has anything to do with it. The package manager now refuses to run, the add/remove software won't,and update manager hangs if I try to update. I tried using the superuser from the command line and I get this response 

sudo: can't stat /etc/sudoers: Stale NFS file handle

trying visudo results in
visudo: /etc/sudoers: Stale NFS file handle

Does anyone have any ideas?

---

### Post by kerry_s on 2009-06-30
boot into the rescue mode. type:
[B]apt-get remove --purge sudo
apt-get install sudo[/B]

only do this in the rescue mode were you are root!

---

### Post by SuperCave on 2009-06-30
I tried Logging into rescue mode at start up, but It gives the message that this option is not available with the cd (I'm Running from an SD card but it doesn't know the difference) So the solution (as you have layed it out) is to remove and reinstall SUDO, but I have to be root. Is there another way to get at root?  Is Rescue mode the only way with (X)ubunto?

---

### Post by SuperCave on 2009-06-30
I Think I'm In trouble now. I logged in as root executed the apt remove purge now it will not install sudo.
this is the output
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gdm: Depends: gksu (>= 1.0.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
on the brighter side I no longer get the file handle message, so sudo might acutally workif I can install it?

---

### Post by kerry_s on 2009-06-30
do: **apt-get install gksu sudo**
hopefully that will fix that error and your sudo.

---

