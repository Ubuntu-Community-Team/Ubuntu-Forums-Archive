---
title: "Disabling touchpad whilst typing"
date: 2010-04-07
forum: Hardware
---

### Post by Scutchamer on 2010-04-07
Ok so this has been doing my head in for a while. I'm used to linux had k and xubuntu installed on my desktop for a while and zenwalk on my laptop. Anyway I've put ubuntu NBR on my netbook (ASUS eeepc 1005HA) but it just won't disable the touchpad at all whilst typing, I've followed this guide 
[Perfect Jaunty on the ASUS eeePC 1005HA]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/") I've done everything except remove the NBR interface. I've tried every post on this forum and I've followed [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

However syndaemon runs on startup but does nothing (I can't find where this is set to run), I've found if I tick disable touchpad with gysynaptics it will re-enable after I stop typing, I have tracked this down to this syndaemon instance, if I run syndaemon in terminal without -d it says it's enabling and disabling the touchpad as you type as you would expect but doesn't but it does tick the box in gsynaptics.

I've tried to run it with the -S (and -s) command (this is listed on the help.ubuntu link and in man syndaemon but in terminal...

foo@bar:~$ sudo syndaemon -d -t -S
syndaemon: invalid option -- 'S'
Usage: syndaemon [-i idle-time] [-m poll-delay] [-d] [-t] [-k]
  -i How many seconds to wait after the last key press before
     enabling the touchpad. (default is 2.0s)
  -m How many milli-seconds to wait until next poll.
     (default is 200ms)
  -d Start as a daemon, i.e. in the background.
  -p Create a pid file with the specified name.
  -t Only disable tapping and scrolling, not mouse movements.
  -k Ignore modifier keys when monitoring keyboard activity.
  -K Like -k but also ignore Modifier+Key combos.
  -R Use the XRecord extension.

According to the package manager I have the latest version of xserver-xorg-input-synaptics installed.

I've resorted (shamefully) to the default windows XP install for the time being as I can't use facebook and hotmail in linux (it keeps clicking the back button somehow and deleting whatever I'm typing).

This problem has been bugging me for at least two months ubuntu had the advantage of speed over windows but as I can hardly use the internet it's currently a bit of a waste of time in my eyes.

---

