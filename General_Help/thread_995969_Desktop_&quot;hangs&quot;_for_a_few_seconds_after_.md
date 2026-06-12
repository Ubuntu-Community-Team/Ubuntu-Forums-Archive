---
title: "Desktop &quot;hangs&quot; for a few seconds after logging in"
date: 2008-11-28
forum: General Help
---

### Post by BobXFett on 2008-11-28
Hi, all. This will be my first post on these forums. I've found lots of useful threads in the past and this is the first time I've run into an issue that I can't find the solution for.

Disclaimer: my Linux experience is low-to-medium.

My problem is as follows: When I log into my user account and my desktop begins loading, first there is a long pause with just a blank screen (with a mouse cursor) where nothing visible happens. Then I see the desktop wallpaper, the top bar menus and quick launch, my other panel applets (monitors for cpu usage, temp, etc.) and then the animated spinning mouse cursor indicating that something is loading. At this point in the loading process, the animated mouse icon freezes for a number of seconds (I haven't timed it, but let's say 10 seconds or so) and none of the temp/usage monitors animate. After the freeze, the "task tray" icons (clock, sound mixer, etc) appear, and my panel applets update in realtime as usual. The desktop icon that I have also appears at this point (just a folder saved in the desktop).

I'm not entirely sure when this issue began, but I know that it didn't occur with the fresh install of Ubuntu.

At this point, I'm thinking it's either an application that I have set to run on start up, or an update that has been applied to my system that is causing the hang. It's getting pretty annoying, since I know there has to be some way to track it down and fix it, but so far I'm drawing a blank.


Some information about my system (everything I can think of at the moment that might be pertinent):

Hardware: Dell Inspiron 1420 laptop (specifics available if needed)
OS: Ubuntu 8.04 (Hardy)
Kernel: 2.6.24-22

Startup applications from "Sessions" dialog:
jockey-gtk (check for new drivers)
evolution-alarm-notify
gnome-do
nm-applet (network manager)
gnome-power-manager
system-config-printer-applet
pactl load-module module-x11-xsmp (for audio)
syndaemon -d -t -i .333 (disables touchpad tap-clicks while typing)
trackerd
tracker-applet
update-notifier
xdg-user-dirs-gtk-update
gnome-at-visual -s
gnome-volume-manager
wallpaper-tray (rotates wallpapers)

Other software that could be involved:
compiz-fusion

Panel applets:
CPU Frequency Scaling Monitor 2.22.2
System Monitor 2.22.2
sensors-applet 2.2.1



My first question is, is there some kind of log in the system that I can review that might help me identify what process it is that is taking so long to load? If so, where would that be stored?

What is the best method for me to go about nailing down what it is causing the hang?


Thanks in advance

[EDIT]
Updated/corrected some of the timeline of what happens upon login.
[/EDIT]

---

### Post by impact on 2008-11-28
If you disable compiz, does the problem go away?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292376](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292376)

---

### Post by evildragon2 on 2008-11-28
The system log is in System->Administration->System Log.

---

### Post by BobXFett on 2008-11-28
> **impact said:**
> If you disable compiz, does the problem go away?

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292376](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292376)

This is a dumb question, but how do I disable compiz without uninstalling it?


[EDIT]
Disregard, I found that.
To answer the question, no, disabling Compiz doesn't make a difference. I loaded up with default (metacity) and I still have the hang. The only visible difference was the mouse cursor didn't hang on the loading animation, but the system still was delayed in loading.
[/EDIT]

---

### Post by impact on 2008-11-28
Ok, looks like you will have to examine system logs. Each line starts with a timestamp, that should help you locate the problem.

---

### Post by everthonvaladao on 2009-01-19
I think this "hang" has something to do with Evolution Alarm Notifier fetching appointments from the web (i.e. Google Calendar), because if you disable it from "Preferences > Session > Initial Apps" the hangs goes away.

Tip: if you click on the clock/calendar applet and it freeze the gnome-panel for the same reason, just run:

```
'evolution --force-shutdown'
```

[]'s

P.S.: take a look at
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/203527]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/203527")

---

