---
title: "OpenGL not using direct rendering"
date: 2015-02-14
forum: Hardware
---

### Post by Kymus on 2015-02-14
This is the error I get when I open Steam.

Background:

XCOM: Enemy Unknown was [crashing repeatedly during a certain part]("http://steamcommunity.com/app/200510/discussions/0/522730699788544934/"), and the devs said to "upgrade/install xorg edgers ppa and nvidia 340.17 drivers".

K, so I go through that process, add the PPA, update my drivers, and the process fails (and the error report leading me to this bug report [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1401597")).

I've tried switching drivers to see if that does anything (304 proprietary, 331 proprietary, 331 open source, 340 open source) and that's done nothing.

I've tried searching for other posts about this problem and the most recent one is [this]("http://ubuntuforums.org/showthread.php?t=2255341"), but that involves AMD hardware, so I assume these problems are unrelated.

At this point, I'd just be happy to go back to how things were, buggy play or not, since now the game will no longer load.

---

### Post by Yellow Pasque on 2015-02-15
I would try to remove all nvidia drivers, but first, you have to kill nvidia-persistanced: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1401591/comments/14](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1401591/comments/14)
(Note: you can install/use htop if you're not good with PID's).

After you have everything cleaned, I would recommedn this PPA: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by Kymus on 2015-02-15
Hi Temüjin, thank you for the input.

In trying to identify the id of the process, the poster says to do ***ps -e | grep nvidia-persistenced***, but after running that line, nothing happens (literally) and I am just given a new command prompt.

Suggestions?

(addendum: if you wouldn't mind, I'd appreciate documentation on how to remove the drivers as well. Unless I'm really dense (maybe!), I'm only finding tutorials from 2010 - 2012. Not sure if they are still relevant)

---

### Post by Kymus on 2015-02-15
Ok, this is a bit out of my level of experience, but I installed htop and tried searching for nvidia and nvidia-persisted. This may be an incorrect assumption, but I do not think it is running as the search turned up nothing, but when I did the same search for a process that is running (dropbox), that was highlighted and shown.

---

### Post by Yellow Pasque on 2015-02-15
Then perhaps the bug does not affect you.
What happens when you try to install a new driver?

> I'd appreciate documentation on how to remove the drivers as well
If it was me, I would just run:
```
sudo apt-get purge nvidia*
```
That works for me on Debian. I don't know how Ubuntu names/structures its packages these days.

---

### Post by Kymus on 2015-02-15
Well this is interesting. Things are fine now o_O.

Some details:

I ran ***sudo apt-get install nvidia-346***, and halfway through there was an error popup and my system froze. REISUB, tried again. This time, everything completed without issue (before I was given the error that the process (nvidia) was running and the installation was halted). 

I loaded steam, got that error notice about OpenGL, checked my driver version and saw that I was using the open source drivers, so I switched to the nvidia 346 open source drivers, ran steam again, no error. Load up xcom, and so far so good.

If things stay stable for the rest of the day, I'll mark the thread as solved.

Thanks again :)

---

