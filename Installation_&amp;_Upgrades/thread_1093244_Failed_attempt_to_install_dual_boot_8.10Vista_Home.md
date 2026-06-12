---
title: "Failed attempt to install dual boot 8.10/Vista Home"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by JerryI on 2009-03-11
I have tried to create a dual boot system for Ubuntu 8.10/Vista Home, starting by shrinking my Vista space to leave 40GB unallocated for Ubuntu.  The computer is amd AMD64 with 2GB RAM.  First I created a Ubuntu i386 disk and got all kinds of buffer read/write errors in spite of a valid integrity check and a valid hash check to make sure the iso file size was right.  So then I created a Ubuntu amd64 install disk and tried again.  This time no errors were reported, but the install only got to the big ugly brown picture with no further instructions (hung overnight).  An interesting twist is that my system is dual monitor and that everything up to the final appearance of the big brown picture was on the left monitor, but the picture appeared on the right monitor.

I have very little experience.  Any suggestions would be appreciated.

---

### Post by t0mppa on 2009-03-11
> First I created a Ubuntu i386 disk and got all kinds of buffer read/write errors in spite of a valid integrity check and a valid hash check to make sure the iso file size was right.

If by disc you mean a CD/DVD, try using Unetbootin [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") and putting the install files on either a hard drive partition or a USB stick, that are much more reliable in order to get rid of the buffer read/write issues.

> So then I created a Ubuntu amd64 install disk and tried again. This time no errors were reported, but the install only got to the big ugly brown picture with no further instructions (hung overnight). An interesting twist is that my system is dual monitor and that everything up to the final appearance of the big brown picture was on the left monitor, but the picture appeared on the right monitor.

Might want to try the alternative installer [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), which doesn't use Graphics mode and save fighting with the drivers until after you've installed the OS first.

---

### Post by JerryI on 2009-03-11
I have done better today, but after 10 hours or so I'm still not there.  Found article that said to shrink my vista space, which I did, before trying to install ubuntu.  Got much further through the installation and thought it was installed.  Accessed my router, but web browser would not come up.  Wrote copious notes in gedit, but they evaporated in one false keystroke and I was never able to find the notes again.   Saw 'Installing System' but never got to a reboot.  No apparent progress after an hour or so; tried to get cd door to open, but it wouldn't.   Finally logged off and ubuntu came back up and wouldn't let me log in with my name and password.  It automatically logged in as user ubuntu.  I shut down the system and it rebooted into Vista which is where I am composing this lament.  I guess I'll screw around with this for another couple hours before I declare it hopeless and try to find an XP computer because it's the only stable os I've seen since msdos 3 or so.  It's been a very unfruitful 3-4 days of effort.

---

### Post by JerryI on 2009-03-11
Thanks t0mppa

I was able to use Wubi, and it worked like a charm.  I am very close, but I have hit a major snag.  When I boot Ubuntu, it won't accept my username, password input.  I fear I might have to  start all over.  Maybe even reformat and install Vista from scratch.  If so, I have at least a week of work to get back to where I was a couple days ago.  This is probably more discouraging than the last couple days of drudgery and failures that I have experienced.

---

### Post by lindsay7 on 2009-03-11
See if this gets your password and username back.

You could try this.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by JerryI on 2009-03-11
Thanks Lindsay.  I learned how to boot into recovery mode and find my name was gai not jerry.  I'm sending my first post without Vista.  Hooray!

---

