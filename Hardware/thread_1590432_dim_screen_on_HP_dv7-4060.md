---
title: "dim screen on HP dv7-4060"
date: 2010-10-07
forum: Hardware
---

### Post by jcphil on 2010-10-07
In Ubuntu, the screen is annoyingly dim. There is a keyboard control for this, but it doesn't do anything in Linux. There is an ATI Catalyst Control center installed, but if I try to use it, it errors out and says the driver is not installed. A look at Jockey tells me that it *is* installed. So, how can I adjust the brightness?

I have similar problems with the audio. The volumes are set at maximum in Alsa and everywhere else, but the sound is very low. Anybody have any ideas? Both brightness and sound volume are fine in Windows.

---

### Post by Carl.Spackler on 2010-10-08
I have the same notebook. What version of Ubuntu are you using? Also, are your function keys set to use the function key or the quick key? This is a BIOS setting and can be changed. I have mine set to use the quick keys and I do not have the same issue that you have. Also, due to the switchable graphics in our machines, by default both video chips are powered up. Just so you are aware it will discharge your battery quicker. Depending on what version of Ubuntu you are using there are a couple of different ways to resolve this. Do a search for hybrid graphics and linux and you will find many posts.
 
The sound issue I had was fixed by using the alsa-gui-mixer. I looked for the bookmark I thought I had but it is missing - sorry!

---

### Post by brandonmpace on 2010-10-10
I have the DV7-4069wm

Mine are set to not use the Fn key, just the quick keys, and they all work correctly except the brightness.

This is on 10.04.1 and 10.10.

The brightness applet doesn't change it either, leaving me with no control over the brightness.

This may be related to the only other problem I am having.
Both video cards power up, and even with the ATI driver installed it defaults to the HD4200. It calls the HD5650 an unrecognized device in the ATI control center.

I don't care enough to power down the other video device manually, I'm waiting for a fix. I at least want a tool to power down the card not in use with a click..

Is there a bug report for this? I'll gladly add my logs or any needed info if there is one.

---

### Post by Carl.Spackler on 2010-10-12
See this page:
 
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
 
there is a part where the commands are presented to power down the unused card. If you have 10.10 installed you can just use the commands below, otherwise there are some other steps you need to perform.
 
Looks like:
 
```

$ su 
$ mount -t debugfs none /sys/kernel/debug 
$ cd /sys/kernel/debug/vgaswitcheroo 
$ cat switch* # to see which card is active* 
$ echo DDIS > switch* # to go to discrete card (log off and then log in after this command)* 
$ echo DIGD > switch* # to go to integrated card (log off and then log in after this command)* 
$ echo OFF > switch* # to just power off the card you aren't using*
```
 
Apparently, you cannot use the ATI drivers with this because it does not use X in the way that we have been used to.

---

