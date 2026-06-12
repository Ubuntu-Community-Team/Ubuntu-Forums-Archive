---
title: "Can't boot up with Feisty after latest updates"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by kstarkey1 on 2007-04-13
Hi all,
I've been running Feisty beta for over a week now with barely any problems.

I'm a bit of a newbie.  (others I hear who say that seem to know way more than me)

Last night at around 10:40pm (EST) I run the update manager.  There were 24 (if I remember corrrectly) updates and I chose to accept them all.  They downloaded and installed fine.  It said I needed to restart, but since I was going to bed I just shut down.  When I got up this morning and turned on my Asus laptop, I get the splash screen, but the orange bar never advances.  After a minute or so I get a 'ash' screen I've never seen before and the message I get is:

[INDENT]/bin/sh: Can't access tty: job control turned off
(initramfs)[/INDENT]

From this point on I'm totally lost.  I don't have a clue how to proceed.

Am I totally screwed, or can I rescue my system somehow?

If anyone can advise, I would be greatly indebted to you.

Kind regards,
Kevin

---

### Post by themunkee on 2007-04-13
ditto. I can boot other kernels, but the nvidia driver the conflicts with the version in x or something

---

### Post by kvonb on 2007-04-13
How far in the boot process do you get?

Wait till it's finished disk access, then try pressing <CTRL><ALT><F1> to go to the first virtual terminal and see if you get a login prompt.

If you do, login with your normal account and type this:

```
sudo apt-get update
```

wait till it's finished......

```
sudo apt-get upgrade
```

That will download and install any updates that have happened since the last time you did it.  Which should hopefully fix up any broken ones.

When it has finished, reboot and see if it works.

If you get a graphics driver problem, go to the VT again, login and type:

```
sudo dpkg-reconfigure -phigh xserver-xorg

```

....and select the "vesa" driver and the screen resolutions that you need.  You can change back to an accelerated (restricted) driver once you are back on the desktop.

If you do get back up, I would suggest ignoring any more updates until Feisty is actually released :).

Regards, Kev :)

---

### Post by themunkee on 2007-04-13
I believe this is the same issue:

[http://ubuntuforums.org/showthread.php?t=408057&highlight=2.6.20-13+can%27t+access+tty](http://ubuntuforums.org/showthread.php?t=408057&highlight=2.6.20-13+can%27t+access+tty)

---

### Post by kstarkey1 on 2007-04-13
Thanks!

I'll give it a go.

Kind regards,
Kevin.

---

### Post by themunkee on 2007-04-13
Thanks, kvonb, but it didn't work.

I followed the instructions on getting it to load the .bak file and that fixed it all. I didn't need to play with the xorg files.

---

### Post by kstarkey1 on 2007-04-13
Thanks themunkee, for the heads-up on the other thread.  That's sounds like the solution.  I'll try that .bak solution.

Kind regards all,

---

### Post by kstarkey1 on 2007-04-13
btw, that (.bak) solution from the other thread worked.

thanks again!

---

