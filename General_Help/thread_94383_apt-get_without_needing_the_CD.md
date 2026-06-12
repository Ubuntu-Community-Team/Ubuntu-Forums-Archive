---
title: "apt-get without needing the CD"
date: 2005-11-23
forum: General Help
---

### Post by Mortuis on 2005-11-23
I'm new to Ubuntu, and have been playing around with Ubuntu 5.10 Server.  One thing I've noticed, is sometimes when I apt-get something it will ask me to put the CD in.  I would like to work on this computer remotely, and have other media in the CD drive, is it possable to tell apt-get not to request the CD?

I suspect it would require commenting out the first line of /etc/apt/sources.list, but I was hoping to get some confermation.

---

### Post by Kapre on 2005-11-23
[QUOTE=Mortuis]I'm new to Ubuntu, and have been playing around with Ubuntu 5.10 Server.  One thing I've noticed, is sometimes when I apt-get something it will ask me to put the CD in.  I would like to work on this computer remotely, and have other media in the CD drive, is it possable to tell apt-get not to request the CD?

I suspect it would require commenting out the first line of /etc/apt/sources.list, but I was hoping to get some confermation.[/QUOTE]

Yes sir. That's right. You have to comment the 1st line for apt not to get the apps from the cd. But if you do that you need to have an internet connection so you can download the apps from the repos.

K

---

### Post by Mortuis on 2005-12-20
[QUOTE=Kapre]Yes sir. That's right. You have to comment the 1st line for apt not to get the apps from the cd. But if you do that you need to have an internet connection so you can download the apps from the repos.

K[/QUOTE]
That worked, thanks. :-)

---

