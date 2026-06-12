---
title: "Broken system from 7.10 to 8.04 upgrade failure"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by rstunin on 2009-05-19
I had been using 7.10 for a long time and decided to upgrade since it had reached EOL.  First I did a network upgrade which died do to a network outage.  As suggested on the upgrade page I ran "**dpkg --configure -a**" from a rescue shell and was able to restore the system enough to be able to start a terminal session to run "**gksu "sh /cdrom/cdromupgrade"**" and start a CD based upgrade.  After encountering a number of broken packages this upgrade stalled and locked up the computer.  After restarting the computer I got a gray checked background and this error message:

**No servers defined in the configuration file and XDMPC was disabled.  This can only be a configuration error.  GDM has started a single server for you.  You should log in and fix the configuration.  Note that automatic and timed logins are disabled now.**

When I press OK it just cycles back to this screen instead of starting the GUI.  A thread on another forum suggested logging into a rescue shell and doing the following:

[B]apt-get remove --purge gdm
apt-get install gdm[/B]

This helped the questioner but doesn't seem to work for me.  Nothing seems to happen when I try to remove GDM and when I run install it tells me I already have the newest version installed.

I've been beating my head against this for a few days now and am out of ideas.  Is there something in particular I should be looking for in the GDM config files?  Looking through them doesn't show anything obvious to my untrained eye.  Any ideas would be appreciated.

Thanks,
Rick

---

### Post by zvacet on 2009-05-20
Did you fixed broken packages?If not then in terminal

```
sudo apt-get -f install
```

---

### Post by rstunin on 2009-05-29
Thanks, I did try that also, but there were packages that it was unable to repair, although they don't seem critical (such as Eye of Gnome, Serpentine, Compiz settings manager).  It seems that the problem is with either GDM or its configuration.

---

