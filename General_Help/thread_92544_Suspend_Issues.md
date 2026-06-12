---
title: "Suspend Issues"
date: 2005-11-19
forum: General Help
---

### Post by redbull on 2005-11-19
I have a Dell Dimension 4700 desktop. When I first intalled Breezy, I was happy to see that suspend and hibernate both worked. However, about 3 weeks ago, suspend just stopped working. I didn't install or change anything (except automatic updates). Now, after I suspend, when I try to resume, the screen never wakes up (orange light doesn't turn green). I think a video module isn't loading right. I have crappy Intel integrated video, if that helps. Funny thing is, if I suspend, and as soon as the process is done, resume everything works. If I wait more that a few seconds, no video. Hibernate works, but I'd rather have suspend, because it's so much faster. If anyone can help, please respond.

---

### Post by wrtrdood on 2005-11-22
Got some issues too but no resolution yet.  I updated several things so it's taking some time to track it all down.  Before I updated KDE to 3.5RC1, klaptop worked perfectly, better than ever before.  Now it sends the laptop catatonic.  No response, no switching screens -- nothing.  I tried suspending via the normal scripts in /etc/acpi/ but have had little luck with that either.  However, the symptoms there have not changed for these scripts since my Breezy install.  Trying to sleep the machine causes it to act as though it will, shutting down everything then comes right back except the screen returns with a nice collection of parallel thin green vertical stripes.  Logs aren't much help.  My update to RC1 was in the same timeframe so it may not be KDE at all.  I'm running a Fujitsu P1120.

[COLOR="Blue"]**Update:**[/COLOR]  Solved several problems by changing ACPI_SLEEP_MODE=standby to ACPI_SLEEP_MODE=mem

---

### Post by redbull on 2005-12-03
bump

---

### Post by redbull on 2006-01-28
Another bump. Anyone? It's been a while and I've read other threads, but no one seems to have posted anying that is the same as my problem.

---

### Post by SwinginStan on 2006-01-31
I have got the exact same problem on a Dell c400! I would really really like to get suspend to ram working!!

---

