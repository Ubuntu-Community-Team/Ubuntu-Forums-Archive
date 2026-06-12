---
title: "Caution with Intel X3100 and 9.04"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by zalberico on 2009-05-02
May not want to update, My story:


I upgraded to 9.04 from 8.10 (breaking my own rule of if it isn't broken don't fix it).  I have the intel x3100 integrated graphics which has been blacklisted for stability issues.

I used a command to get around the blacklist (probably not the greatest idea) and everything appeared to be working fine.  I never ran into any stability issues about playing video with desktop effects, never had any problems at all.  I'm also not that new to gnulinux so I thought whatever happened I could reverse.

Today the screensaver came on and then wouldn't resume to desktop, I tried ctrl alt backspace and got nothing.  I then ctrl alt f2 and logged in and rebooted that's when disaster struck.

It would boot up and then shortly after the grub screen hang at a white blinking cursor.  After trying recovery mode which failed and trying just to boot a few more times I pulled out my live cd figuring I'd just force mount and save the data.

Normally mounting reproduces the standard must force mount error, instead I got this: 
Cannot mount volume.
Unable to mount the volume.
Details
mount: wrong fs type, bad option, bad superblock on /
dev/sdb7, ______ missing codepage or helper program,
or other error ______ In some cases useful info is found
in syslog - try ______ dmesg | tail or so

My attempts to recover data failed and I tried one last time to boot into my old system and this time the screen remained a vibrant neon green before failing.

Luckily I had most of my data backed up.

While I have no information to help someone who is in this situation, perhaps someone on the forums here might, otherwise if you're looking here to see if you should upgrade, I would say wait.

---

### Post by rabbit251 on 2009-05-02
Wow man, that's really rough. I'm using Jaunty with the Intel X3100 and have considered forcing through the blacklist, but maybe I'll wait, considering this anecdote. Best of luck.

---

### Post by rabbit251 on 2009-05-03
I think the updates were sent out yesterday, and now the Intel graphics cards are functional. Compiz is working great over here, and my card was taken off the blacklist automatically.

Unfortunately, I still have no advice for you. What's going on now, are you reformatting?

UPDATE: Some people may still be having issues with the graphics. Check out the comments in [Bug #359392]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/359392?comments=all").

---

### Post by zalberico on 2009-05-26
Yeah I went back to 8.10.  Unless I find some new feature I really want or reason to update I'll probably wait here for a while.

---

