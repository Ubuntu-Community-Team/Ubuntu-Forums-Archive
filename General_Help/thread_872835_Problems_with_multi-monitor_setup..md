---
title: "Problems with multi-monitor setup."
date: 2008-07-28
forum: General Help
---

### Post by CShadowRun on 2008-07-28
Hi, I'm trying to acheive a twin, twinview setup. (So 4 monitors, 2 X Screens.)

like with this command.

```
nvidia-xconfig --enable-all-gpus --no-separate-x-screens --twinview
```

Ok, so it works. I mean i can move my mouse between all displays, and i have 2 sets of panels, and i can drag windows between screens 1 and 2. Or 3 and 4.

Now for the problem.

Basically i'm getting a hell of alot of REALLY strange bugs, i'll list them in the hope that one of them rings a bell.

Panels span across the both screens in each twinview.

Watching a full screen flash movie, it shows only on one display. However only shows one side of the movie.

Pressing the shut down button on the panel makes the computer crash. (Only on Screen 1)

Using the volume control on my keyboard changes the gnome theme (Only on Screen 1) I belive the volume control overlay display window crashes the gnome settings daemon, which resets the system theme.

Compiz fusion makes the system extremely laggy. Clicking the Applications button on the panel takes around 4 seconds to load.

Compiz fusion freewins plugin seems to decide to lock the mouse pointer.

Notification (system tray) is broken on screen 1.

Notification (system tray) icons on screen 0 come up in a window.

I seem to be able to run more than one instance of compiz --replace.

I seem to be able to run more than one instance of emerald --replace

[Here is my xorg.conf](http://www.nomorepasting.com/getpaste.php?pasteid=18504)

Any ideas appriciated. Thanks

---

### Post by CShadowRun on 2008-07-28
I belive this is because of having multiple X screens running. I've tried a few diffrent configurations.

4 X screens (So 4 panels, 4 monitors.)
Pressed shut down button, crash.

I even tried 2 X Screens and my spare monitors disabled, and still crashed when i hit the shut down button.

---

### Post by CShadowRun on 2008-07-29
bump

---

### Post by bodhi.zazen on 2008-07-29
A majority of your issues are due to gnome. It is a shame that after all this time gnome is not so good with multi monitiors.

Try xfce or kde and I bet most of your problems will resolve.

The other part of your issue is with twinview. Often when apps start they are centered, spanned across both monitors. Only 1 monitor is working w/ your movie.

Can you start the application in a smaller window, move it to one monitor, then go full screen ?

---

### Post by CShadowRun on 2008-07-29
Thanks for your reply.

The only things that seem to span are the panels and full screen flash player movies, neither of which are resizable :(

I shall try installing kubuntu through synaptic and checking it out tommorow morning :D

---

### Post by CShadowRun on 2008-07-31
kubuntu appears to be a no :(

I started up kubuntu and straight away it put the update notification icon up in an external window.

It also couldn't see 3 of my hard drives...but yea, anyway.

The bars also spanned both displays, however there was this cool setting to make them shorter, so i set them to 50% size which worked perfectly.

But in any event, yes. Bugs still seem to exist in kubuntu.

---

### Post by CShadowRun on 2008-08-09
Still got this issue. Has anyone actually got a working multiple x screen setup (NOT twinview/xinerama)?

---

### Post by CShadowRun on 2008-08-16
Still got this issue, and i'm not the only one.

[http://ubuntuforums.org/showthread.php?t=156272](http://ubuntuforums.org/showthread.php?t=156272)
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/128735](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/128735)

Why isn't anyone making an attempt to fix this? As much as i'm trying to switch over from windows to linux. Having a quad screen setup in windows is pretty much plug and play. Why is it that there are so many bugs when you go over 2 displays?

---

### Post by CShadowRun on 2008-08-21
bump, still stuck.

---

### Post by CShadowRun on 2008-08-22
bump, notification area is also broken in xfce4-panel, only on secondary screen.

---

### Post by CShadowRun on 2008-08-22
and kicker, kde's panel.

This appears to be a major bug.

---

### Post by bodhi.zazen on 2008-08-22
"Major bug" is a bit of an over statement, although I agree it is annoying.

And as you can tell from the lack of responses there is no "fix". It seems your options are to :

1. File a bug report with Gnome, KDE, XFCE, Xorg, Nvidia, etc.

2. Write the code yourself.

3. Use an acceptable work around.

---

### Post by CShadowRun on 2008-08-22
> **bodhi.zazen said:**
> "Major bug" is a bit of an over statement, although I agree it is annoying.

And as you can tell from the lack of responses there is no "fix". It seems your options are to :

1. File a bug report with Gnome, KDE, XFCE, Xorg, Nvidia, etc.

2. Write the code yourself.

3. Use an acceptable work around.

1) [https://bugs.launchpad.net/ubuntu/+s...el/+bug/128735](https://bugs.launchpad.net/ubuntu/+s...el/+bug/128735)

2) I'm not a programmer

3) I don't know of any workarounds

---

### Post by CShadowRun on 2008-08-23
Found a workaround for the notification area (system tray)

Kicker (kde's panel) xfce, and gnome are broken. However

Fluxbox's fbpanel is not
also, AWN is not.

You have to run one instance for each screen, but hey, it works! :)

---

