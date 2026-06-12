---
title: "Brightness control on Toshiba R830"
date: 2011-07-19
forum: Hardware
---

### Post by brownie3003 on 2011-07-19
Hi,

I'm new to Ubuntu, not new to linux, but by no means an expert. I have put Ubuntu 11.04 on my Toshiba R830. Loving it so far. Major problem is that brightness can't be controlled after laptop has been suspended and then restarted. This is not a new problem for Toshiba's. I've tried following the fix for the r700 posted at the bottom of page 1 for this thread:

[http://ubuntuforums.org/showthread.php?t=1550219](http://ubuntuforums.org/showthread.php?t=1550219)

The problem is that this fix doesn't work for me. I've installed the toshset patch and it works in the command line but behaves really weirdly. After suspend/restart toshset -bl on will change the intensity if I use:
toshset -inten 5
toshset -bl on
or
toshset -inten 2
toshset -bl on

The Fn key still does nothing.

Whereas before suspend Fn keys work and in command line it only requires:
toshset -inten #

to set brightness as expected.

I don't see how the solution with the shell scripts would work for anyone though. -bl just controls the backlight (on or off). -inten controls the brightness of the backlight. Surely on the event which corresponds to brightness up (fn+f7) the program called should query the intensity, and add one to this. Vice versa for brightness down. Now I don't really know much about program writing etc. I've never written a shell script, I've only been dabbling in linux for a couple of years and just following fixes on forums, so I may be missing something obvious.

Any thoughts or solutions would be appreciated!

---

### Post by madmack on 2011-10-20
> **brownie3003 said:**
> Hi,

I'm new to Ubuntu, not new to linux, but by no means an expert. I have put Ubuntu 11.04 on my Toshiba R830. Loving it so far. Major problem is that brightness can't be controlled after laptop has been suspended and then restarted. This is not a new problem for Toshiba's. I've tried following the fix for the r700 posted at the bottom of page 1 for this thread:

[http://ubuntuforums.org/showthread.php?t=1550219](http://ubuntuforums.org/showthread.php?t=1550219)

The problem is that this fix doesn't work for me. I've installed the toshset patch and it works in the command line but behaves really weirdly. After suspend/restart toshset -bl on will change the intensity if I use:
toshset -inten 5
toshset -bl on
or
toshset -inten 2
toshset -bl on

The Fn key still does nothing.

Whereas before suspend Fn keys work and in command line it only requires:
toshset -inten #

to set brightness as expected.

I don't see how the solution with the shell scripts would work for anyone though. -bl just controls the backlight (on or off). -inten controls the brightness of the backlight. Surely on the event which corresponds to brightness up (fn+f7) the program called should query the intensity, and add one to this. Vice versa for brightness down. Now I don't really know much about program writing etc. I've never written a shell script, I've only been dabbling in linux for a couple of years and just following fixes on forums, so I may be missing something obvious.

Any thoughts or solutions would be appreciated!

You see the VALZ line in the last post of that referenced page? That's your problem.
run "acpi_listen" and click on your brightness buttons. see what value you get, then put these instead of the VALZ values.

Mine were "video DD01 00000086 00000000" and "video DD01 00000087 00000000" for brightness up and down respectively.

---

### Post by egal2 on 2012-05-14
at brownie3003:

just a short question. Does everything else work with ubuntu, even the 3G Network?

Thanks

---

