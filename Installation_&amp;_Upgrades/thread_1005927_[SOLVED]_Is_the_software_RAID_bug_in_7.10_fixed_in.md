---
title: "[SOLVED] Is the software RAID bug in 7.10 fixed in 8.04 LTS ?"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by lcason on 2008-12-08
Last year I spent several weekends with the ubuntu-7.10-alternate-i386.iso CD but was not able to make software RAID work correctly on my home file server that has 3 EIDE 120 GB HD, Intel P4-3Ghz CPU on Intel 875P MB . I followed the instructions posted [_[COLOR="Blue"]here [/COLOR]_]("http://kuparinen.org/martti/comp/ubuntu/en/raid.html") (except the Ubuntu version was 7.X then) but kept getting an [_[COLOR="Blue"]error condition[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=4571771#post4571771"). I do remember that I found several other people that had made posts that there was a bug with software RAID in 7.10. As much as I like Ubuntu, I had to get the job done, so I installed CentOS 5 and it worked fine. 

Now that 8.X is out, I'd like to switch back to Ubuntu, but I don't want a repeat of the problems I encountered with 7. Can anyone confirm if the software RAID bug that caused failed installation on 7.10 is fixed in 8.04 LTS? 

Thanks,

Lee

---

### Post by lcason on 2008-12-11
**[COLOR="Green"]BUMP[/COLOR]**

I'll ask again in very simple terms. Anyone know if the bug that was in 7.1 that caused software RAID installation to fail in certain cases has been fixed in 8.X or not?

Thanks

Lee

---

### Post by bsmith1051 on 2008-12-11
What you're describing is "degraded RAID" operation and it's only officially fixed in 8.10.  There is a good workaround for it in 7.10, no workaround at all with 8.04 or 8.04.1, and a "proposed" fix for 8.04.2 (not officially available but easily accessed through Synaptic).  Personally, I like the workaround in 7.10 the best because it's totally automatic!  The official fix, however, is to try-try-try and then momentarily prompt the user if they would like to continue booting in degraded mode; miss the prompt and you have to reboot (and wait 3 minutes) all over again.

Check-out these threads:

MY DESCRIPTION OF THE 7.10 WORKAROUND
[http://ubuntuforums.org/showthread.php?t=716398](http://ubuntuforums.org/showthread.php?t=716398)

OFFICIAL DISCUSSION OF 7.10 WORKAROUND
[https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375)

OFFICIAL DISCUSSION OF 8.04.2 FIX/TESTING
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/290885](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/290885)

---

### Post by lcason on 2008-12-12
Thank you bsmith1051!  I will give 8.10 a try. I don't mind spending the time trying to get this to work as long as I have at least a possibility that it WILL work. You've given me the encouragement to proceed.

=D>

Cheers,

Lee

---

