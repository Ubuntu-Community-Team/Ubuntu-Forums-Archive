---
title: "Problem install on new hp machine"
date: 2008-08-31
forum: General Help
---

### Post by no_bikes on 2008-08-31
I have recently purchased a hp pavilion media center m8525f pc. The machine has a quad core processor, 4 gigs of ram and nvidia graphics card.

The problems are, some times the system won't boot, freezes at different points during start up. And some times it boots problem free. Also about 80% of the time after the system has booted the internet does not work. The other 20% it works fine with out a hitch. the version installed is the newest version of ubuntu downloaded from the web ubuntu web site. The version said it was for 64 bit systems. 

I have ran ubuntu on older machines and never encountered a problem such as this

---

### Post by pytheas22 on 2008-08-31
First of all, check the CD that you used to install Ubuntu for defects.  If it seems to be alright, you may want still to try doing a fresh install of the system (as long as you don't have too much invested in it already), just in case something weird happened during the initial install that's causing the problems.

If after a fresh install things still don't work (or if you can't/don't want to do a reinstall), take a look at the system logs (System>Administration>System Log, or open the file /var/log/syslog in a text editor).  It should provide a clue as to what's going on when the system fails to boot (depending on how far into the boot process the system gets before crashing, it should hopefully be able to start the logging daemon and record whatever it thinks is wrong before the crash).

Let us know if it helps.

---

### Post by no_bikes on 2008-09-01
thank you, I burned a new disk and did a full reinstall, it is now working like a charm.

---

### Post by knattlhuber on 2008-09-01
> **no_bikes said:**
> thank you, I burned a new disk and did a full reinstall, it is now working like a charm.

Now that's really interesting. I have almost the same machine and the same problem.
See here:
[http://ubuntuforums.org/showthread.php?t=897958]("http://ubuntuforums.org/showthread.php?t=897958")

It seemed more like a bug in Ubuntu as there were others with similar problems on launchpad.net

---

