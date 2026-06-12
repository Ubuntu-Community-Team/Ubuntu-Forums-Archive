---
title: "Dual screen, re-plugging VGA device after disconnect doesn't re-enable the VGA device"
date: 2008-09-10
forum: Hardware
---

### Post by iandouglas on 2008-09-10
Hey all,

Posted my progress back in June on getting my Vaio BX-760 working in a dual-screen setup.
[http://iandouglas.com/vaio-bx760-dual-display-in-ubuntu](http://iandouglas.com/vaio-bx760-dual-display-in-ubuntu)
My post there includes my xorg.conf which works fine for my setup, other than the fact that my laptop's monitor is set to 1280x1050 resolution when it can only display 1280x800, so I have a dead zone of 250 px).

If I plug in my LCD monitor before I boot the laptop, or reconnect it later and hit CTRL-ALT-BKSP to restart xorg, the LCD monitor starts up in mirror mode. Once I login, I run:

[INDENT]/usr/bin/xrandr --output LVDS --left-of VGA[/INDENT]

... which changes my mirrored screen to a side-by-side setup. This works great.

If I unplug the VGA connector, the LCD monitor goes into standby mode ("no signal"), and the resolution on the laptop reverts properly back to 1280x800 mode (although the gnome menu bars and 'maximize' resolution seems locked at 1024x768 whenever the laptop is in 1280x800 mode).

What I'm trying to solve:

Plugging the LCD monitor back into the laptop does not re-enable the VGA connection, and the LCD monitor stays in standby mode without any signal. I have to restart xorg in order to get my LCD monitor to start back up, which of course closes all of the applications I'm running.

The xrandr utility properly detects that the LCD monitor is plugged back in, but does not assign a CRTC. I've tried manually adding that to my dual screen setup:

[INDENT]/usr/bin/xrandr --output LVDS --left-of VGA --crtc 0[/INDENT]

(it regularly assigns CRTC 0 whenever I'm properly in dual screen mode)

... but running that command after the LCD monitor is plugged back in does nothing. I've also tried the --auto switch:

[INDENT]/usr/bin/xrandr --output LVDS --left-of VGA --crtc 0 --auto[/INDENT]

... but that didn't do anything, either.

Can anyone help me out here? Having to restart xorg (and thereby closing all apps I'm running) is a serious annoyance since I typically have to take my laptop to one or more meetings every day.

Thanks,
Ian

---

### Post by Jws0001 on 2008-09-21
If I read your post correctly, it sounds like you're having a similar problem to my own.  When I boot up with the monitor attached I can us xrandr to enable it/mirror it/whatever.  However, when I try to connect a monitor after the computer has booted, I can't get it to work.

Instead of restarting the x-server, I am able to get my external monitor to work by restarting acpid:

sudo service acpid restart

Then just use xrandr to re-enable/configure it.  It's not a total solution, in fact I'm looking for a better one, but maybe it will help you avoid having to restart your whole x-server.

---

