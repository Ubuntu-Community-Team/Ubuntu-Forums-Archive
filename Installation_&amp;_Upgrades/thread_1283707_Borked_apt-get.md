---
title: "Borked apt-get"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by Kareeser on 2009-10-05
So, I wanted to try the new notify-osd on Jaunty... except it's not backported because of the unmet deps.

So I downloaded the karmic notify-osd from my mirror and attempted to install it (using dpkg), but it wanted libgtk2.0-0  1.18, while I only had 1.16... so I downloaded libgtk2.0-0 and tried to install it (again, using dpkg), and found that it needed four or five MORE other packages.

So, I gave up.

Except now, I can't install anything because apt still thinks libgtk2.0-0 2.18.1-1 is installed... when it is clearly not.

When trying to correct dependencies using apt-get -f install, apt says I should remove 238 programs, many of which are crucial system packages.

Not so smart.

Any ideas on how I can restore my system?

---

### Post by earthpigg on 2009-10-05
did you do this by putting karmic stuff in your jaunty install and trying to trick it?

if so,

get yourself back to a normal jaunty sources.list and try running 'sudo apt-get update'.

---

### Post by Kareeser on 2009-10-05
Nope... if I changed my sources.list to karmic values, I should end up updating everything, and end up with a karmic system, which I've done in the past.

In this scenario, my sources.list is unchanged, and sudo apt-get update doesn't fix the problem.

---

### Post by Kareeser on 2009-10-06
Bump?

The problem is that my install seems to think dependencies are broken, because a more recent package (libgtk2.0-0) was in the middle of installing, but was aborted.

---

### Post by unutbu on 2009-10-06
Perhaps download the correct jaunty deb from [http://packages.ubuntu.com/jaunty/libgtk2.0-0](http://packages.ubuntu.com/jaunty/libgtk2.0-0)
and then try
```

sudo dpkg --install --force-overwrite libgtk2.0-0_2.16.1-0ubuntu2_i386.deb
```

---

### Post by Kareeser on 2009-10-06
Thanks, unutbu. I was about to give --force-downgrade a try when I got to work (since this was on a work computer), but --force-overwrite seems to be similar.

I'm also planning on inspecting /var/lib/dpkg/status for differences.

I'll let you know.

---

### Post by Kareeser on 2009-10-06
Note for future users: the --force-downgrade option worked.

I retrieved the packages from my mirror: [http://ubuntu.mirror.rafal.ca/ubuntu](http://ubuntu.mirror.rafal.ca/ubuntu)

---

### Post by unutbu on 2009-10-06
Thank you for the update, Kareeser, and glad you got it fixed.

Just out of curiosity, did the --force-overwrite fail to work, or did you try the --force-downgrade first?

---

### Post by Kareeser on 2009-10-06
I tried just the one. To be honest, I think both options would have achieved the same effect.

---

