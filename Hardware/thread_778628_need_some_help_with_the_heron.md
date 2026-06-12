---
title: "need some help with the heron"
date: 2008-05-02
forum: Hardware
---

### Post by rogier.de.groot on 2008-05-02
Hi all,

over the last few days I've been trying to make Hardy Heron work on my systems - a new compaq laptop and an older pc. Both have had, and continue to have, problems however.

First I tried running the x64 livecd on the laptop. HAL wouldn't start. I tried restarting hald and dbus, and finally tried running hald in verbose mode. Turns out it was missing 'fdi-cache' or somesuch (working from memory here). Tried generating that with hald-generate-fdi-cache (or somesuch), but that didn't work either. Couldn't start the installation or anything else without HAL, and the livecd crached after a short time.

Finally managed to get heron installed using the alternate cd, which runs fine, ndiswrapper lets me use wireless aswell. But ndiswrapper doesn't load properly at boot time. The 'ssb' module gets in it's way. I know this because if I rmmod it and then reload ndiswrapper my wireless works. I've tried blacklisting ssb, b43, b44 and b43legacy modules in /etc/modprobe.d/blacklist but it still won't work. I realise I could just put those rmmod/modprobe lines in /etc/rc.local or something, but that just seems like a dirty hack. There ought te be a better way.

On the older pc, which has an intel 82845G/GE/GL video card with an old compaq V510 CRT attached to it, there were video issues. The previous (linux mint) installation had used the 'intel' driver, but that want to run in some weird video mode the monitor doesn't support (1280x768@43Hz, I think). I haven't a clue why it does this, the X.org log file indicates it detects the modes the monitor does support (1024x768@60Hz) just fine. Trying to override it in xorg.conf doesn't work either. Using the 'i810' driver gets me the right resolution, but the graphics seem slower.

There's also an issue with the sound card (also intel, same chipset as both are on-board) which doesn't respond to the volume changing. The master volume setting doesn't affect anything (as far as I know), but opening up the volume manager and changing the 'PCM' setting does.

I'd like to fix these issues - well, the wireless problem I can fix, but I'd like a better way of doing it. I hope someone can help me out, I'd appreciate it.

---

