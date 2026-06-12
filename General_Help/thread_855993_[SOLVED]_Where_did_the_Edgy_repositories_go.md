---
title: "[SOLVED] Where did the Edgy repositories go?"
date: 2008-07-11
forum: General Help
---

### Post by NT4usB on 2008-07-11
Updating tonight and I get a bunch of:
...Packages.gz: 404 Not Found [IP: 91.189.88.46 80]

[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) Doesn't show Edgy anymore.

Don't think my sources.list has changed. I looked back at a sources.list I had from a year ago and it's the same.
What did I mess up?
```
ct@wimp:/etc/apt$ cat sources.list

deb http://us.archive.ubuntu.com/ubuntu/ edgy main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main universe multiverse restricted

# deb http://us.archive.ubuntu.com/ubuntu/ edgy

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu edgy-security main universe multiverse restricted
# deb http://security.ubuntu.com/ubuntu edgy-security

# deb-src http://www.debian-multimedia.org sid main
# deb http://download.tuxfamily.org/3v1deb/ edgy 3v1n0
```

---

### Post by dcstar on 2008-07-11
> **NT4usB said:**
> Updating tonight and I get a bunch of:
...Packages.gz: 404 Not Found [IP: 91.189.88.46 80]

[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) Doesn't show Edgy anymore.
.....

Doesn't support for non-LTS versions end after a certain period?

---

### Post by iaculallad on 2008-07-11
Try changing your download server.

System->Administration->Software Sources, under the "Ubuntu Software" tab -> "Download From:" -> "Main Server". Click on close then click on reload on the next window that pops up.

When the task is finished, open your terminal and:

```
sudo apt-get update && sudo apg-get upgrade
```

EDIT: [Support ended April 2008]("https://wiki.ubuntu.com/Releases")

---

### Post by sdennie on 2008-07-11
From wikipedia:

Ubuntu 6.10 (Edgy Eft), released on 2006-10-26,[64][65] was Canonical's fifth release of Ubuntu Linux. Ubuntu 6.10's support ended on 2008-04-25.

---

### Post by dcstar on 2008-07-11
> **vor said:**
> From wikipedia:

Ubuntu 6.10 (Edgy Eft), released on 2006-10-26,[64][65] was Canonical's fifth release of Ubuntu Linux. Ubuntu 6.10's support ended on 2008-04-25.

Can't let old releases hog server space around the planet, by the look of it (and that's a policy I agree with).

---

### Post by NT4usB on 2008-07-11
Well carp!
I like Edgy (and I don't relish the idea of rebuilding the whole system from scratch...)
Tried the update manager thingy and it blew up...  same errors.
(Already tried the Main repositories too)
I had been getting updates, software, etc. as recently as 12 June. If support ended in April, wonder why that is?
This is disappointing...
Guess this means my Feisty box will be junk soon as well.
I've tried Gutsy. Actually built a box for mom with Gutsy... big mistake. Without a doubt the most pita box I've built to date. So much for impressing dad (Mac user) with the 'other' OS.
Tried Hardy too. It's worse. Might as well be using Windows as that.
Guess it's time to go distro shopping.

---

### Post by sdennie on 2008-07-11
> **dcstar said:**
> Can't let old releases hog server space around the planet, by the look of it (and that's a policy I agree with).

Well, I don't think it's really a disk space issue, it's a maintenance issue.  For instance, the last official update (from kernel.org) to 2.6.22 (the Gutsy kernel) was just before October 2007.  Keeping a kernel that old up to date and patched is a non-trivial task.  After a while, it's just easier to drop support for it and tell users to upgrade.

---

### Post by dcstar on 2008-07-11
> **vor said:**
> Well, I don't think it's really a disk space issue, it's a maintenance issue.  For instance, the last official update (from kernel.org) to 2.6.22 (the Gutsy kernel) was just before October 2007.  Keeping a kernel that old up to date and patched is a non-trivial task.  After a while, it's just easier to drop support for it and tell users to upgrade.

There will be many issues, but if you think about how many mirror repositories there are around the place, and the amount of storage that obsolete software releases would waste, then it isn't insignificant.

I know Sysadmins **hate** old stuff clogging up their resources (because I am one of them......) especially when so many new things are competing for space on these very same servers.

I used to use Slackware 0.0.x releases, but I don't expect them to be found in my local mirrors.......    ;-)

---

### Post by sdennie on 2008-07-11
> **NT4usB said:**
> Guess this means my Feisty box will be junk soon as well.


I think you still have a good 4 months left before Feisty become EOL.

> 
I've tried Gutsy. Actually built a box for mom with Gutsy... big mistake. Without a doubt the most pita box I've built to date. So much for impressing dad (Mac user) with the 'other' OS.
Tried Hardy too. It's worse. Might as well be using Windows as that.
Guess it's time to go distro shopping.

I'm surprised to hear that.  You should post the problems you have had with Hardy and see if people can help (I recommend slowly making separate well titled threads so that you are more likely to get help).

Anecdote: I recently visited my parents and got upset trying to use their XP machines.  I installed Hardy on every machine in the house and they have been quite pleased with the results.  You can't just install and leave.  You have to act as an OEM: Install it, configure it, and make it user friendly for the target audience.

---

### Post by sdennie on 2008-07-11
> **dcstar said:**
> ]
I used to use Slackware 0.0.x releases, but I don't expect them to be found in my local mirrors.......    ;-)

Whoa whoa whoa...  Are you saying I can't get updates to my Slackeware 3.0 that I got from the back cover of a Unix book?  This is quite vexing...  ;)

---

### Post by NT4usB on 2008-07-26
Ok, so after swiping some space from swap and increasing root from 5GB to 6GB, I had enough freespace for upgrading.
A couple hours of downloading and fixing broken packages, I'm now running Feisty on this box.
All in all, not nearly as painful as I expected, given the two year old install. 
btw, there are repositories for the legacy OS. Found this in the Wikki.
[http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/)...

---

### Post by ^rooker on 2008-08-09
Sorry for waking a closed thread, but in case someone stumbles over this, it might be useful to know that there *is* a place where end-of-life repositories for ubuntu are still available:

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)


I'd recommend making a local copy of such a repository in case someone wants to stick to her/his current version of Ubuntu. 
Not having "forced upgrades" is actually something I've mentioned as a plus for Linux (in comparison to Windows), so I was negatively surprised to run into this hazzle. :(

---

