---
title: "Hard drive dying?"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by jamyskis on 2007-02-11
Hi all,

I have two hard drives, a 200GB for Windows (exclusively for games that won't run under WINE) and a 40GB for Ubuntu. Recently I had another go at installing Edgy, with my previous attempt at it being abortive after it continously crashed on me. Alas, I had the same problem again, but I persevered, even though many of the crashes came while the hard drive was being written to.

Now, the last time I tried installing Edgy, it was on a 20GB partition of the 200GB hard drive. This time, the 40GB is dedicated to it. With the regular crashes, I've been forced to run an fsck.ext3 on the drive every time using my 6.06 live CD (I only have an alternate 6.10 installer CD, and it's a pain trying to call up a shell without the drive being mounted). 

Now, I've only just reformatted and reinstalled 6.10, hoping that would do the trick, until it crashed again. Now running any KDE application (Skype, KControl) thrashes out the hard drive, Skype reports a "bus error" and trying to remove the whole KDE libraries and associated programs just locks up Synaptic, and consequently hangs the whole computer - can't switch to another tty or anything.

Everytime I run a scan on the drive, it comes up with a series of errors along the lines of:

Error reading block 196981 (Attempt to read block from filesystem resulted in short read).  Ignore error?

Regardless of how many times I format it or sort it out. It is possible that my 40GB has finally decided to give up the ghost, or is there another explanation for this? The strange thing is that all this came about at the moment I decided to try upgrading to Edgy again. I haven't tried going back to Dapper just yet, as I've gotten quite attached to AIGLX and Beryl.

Would be grateful for any explanations that anyone could offer...more info available if needed.

Thanks in advance,
J

---

### Post by budgie9 on 2007-02-11
It would seem you have some bad blocks on the drive, which is not being corrected. I would suggest formatting it a few more time, it does no harm by the way, and see if it corrects itself. It could be the start of a disk failure or the surface coating becoming damaged. From past experience it is not unusual for a reinstall of software to show such errors up. Sometimes an unused file can be located where it is damaged and is not being called so it is not spotted as being a bad sector. 
If you keep seeing these errors and they don't correct, or get worse dump the drive to be safe.

---

### Post by RandomJoe on 2007-02-11
I would say that yes, the drive is probably dying.  I had similar error messages on the few drives I've had die over the years.  They generally started out just hesitating a moment until one or two of those messages appeared, then going on.  Slowly building until you get slews of them and nothing works.

I believe those messages get logged in /var/log/messages or /var/log/syslog - you may well find many more there, corresponding to crashes.

I will say that I've had one or two drives over the years that gave those messages (usually just one or two) very sporadically but otherwise worked fine.  However, any drives that kicked them out regularly didn't last long.

Generally, the drive has sectors dying for whatever reason (head crash, material flaking off, etc) and the extra space the drives have to automatically map in to replace bad spots is used up.

I suppose it's also possible the drive controller is flaky or dying, but I've never had that problem.  If you're using the same controller to run the other drive, that would pretty well rule it out.

---

### Post by jamyskis on 2007-02-11
Thanks guys. I've already tried reformatting this drive several times with no success, and the drive controller seems fine as the 200 gig drive is doing fine. As a precaution I've taken out the 40 gig, resized my NTFS partition and reinstalled Edgy on a 25 gig partition. It looks to be fine so far, but the problems usually really kick in about a day in...

---

