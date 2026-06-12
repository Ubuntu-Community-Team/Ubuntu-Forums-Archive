---
title: "audigy driver install issues"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by Ryokukitsune on 2007-09-30
well I've gone threw the forums and looked for a solution on this subject however I don't really understand much because this is way over my head. As I write this I'm reinstalling Ubuntu because something went horribly wrong and my desktop environment went on a vacation and I don't know how to fix this short of a clean install. after thats done, problem averted, universe saved... or is it?

I have my Audigy 2 X-Fi card and the Beta drivers but they don't seem to work, I have 7.04 (or what ever install is out as of 9/30/07) I get an error which says that &#8220;the driver is for a 64bit system&#8221; and it closes, I chanced a &#8220;-i&#8221; to a &#8220;-m&#8221; in the installer and get a message that &#8220;my system doesn't have a compatible product&#8221; (note error messages aren't exact since I'm doing a clean install) the card is installed it apparently just doesn't see it and i don't know how to trouble shot this. 

from what I've discovered in the forums a few people have &#8220;patch&#8221; installs or diff installs which seem to be compatible but I'm drowning in the technical stuff and I dont know what to do Linux is a new beast for me. Can someone please help me?

EDIT: i'm not useing the beta, that would just be silly for a newb wouldnt it. clarification made... check.

---

### Post by aldeby on 2007-10-02
Drivers unfortunately often have issues with 64bit platforms due to lacking support on their part. 

First of all I do not think Ubuntu Gutsy 7.10 beta would be a bad choice, even if you are a newbie. Ubuntu team is very professional and this distribution seems to me fairly stable, so you should not get into severe problems with that. Furthermore Gutsy laptop support is far much better speaking of device drivers and power management.

Anyway there is a simplier way (also because beta version of alsa drivers is still not included), you should install beta drivers from alsa, this way:

```

# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel

$ cd alsa-driver
$ ./hgcompile

# make install-modules
# alsaconf
# reboot 

```

---

