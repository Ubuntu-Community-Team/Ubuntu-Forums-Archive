---
title: "Alt keys sometimes fail until I rerun setupcon -k"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by gpongo on 2007-09-26
I have a strange problem with my IBM thinkpad 600 (which worked fine under an old Mandrake version, and under Debian Sarge, before I switched to Fiesty Fawn a few months ago).

Sometimes, when it boots up, the ALT keys don't work. If I run xev or xkeycaps, they don't register anything (a few other keys may not work as well, like pgup, pgdn, prtsc). Most of the keys are fine. If I boot straight to the console, this also sometimes happens, and showkey also doesn't display anything when I press either ALT key.

Anyway, I can fix it from a console window. (From X, I can use xmodmap to map any working key into an ALT key, and then I can switch over to a virtual display and get a console window.)

All I have to do is run setupcon -k from the console window, and the I run showkey. In the first couple of seconds, the alt keys don't work, and then they start to work.

If I don't run setupcon, occasionally the ALT keys will start working again. On the other hand, sometimes the ALT keys are working fine in X, and then all the sudden they quit.

I would guess that about two thirds of the time, the ALT keys work OK on bootup.

Does anyone have any ideas on what I should do to get the ALT keys always working on startup? It is rather annoying.

Regards,
Greg

---

### Post by gpongo on 2007-09-27
OK, I think I fixed it. I figured out that /bin/setupcon was a bash script (duh). During the console setup of the keyboards, it uses /usr/bin/ckbcomp (a perl script) to convert X keyboard definitions into loadkeys (console keyboard) definitions. I guess this makes things easier by having only one set of keyboard definitions; a user just has to change the X set to get the console changes to take effect, too.

Anyway, during the keyboard (input) analysis, it looks at files in the /etc/X11/xkb/rules/ directory. The xorg file there (since ubuntu uses xorg) has a list of allowable models (under !model = geometry). I saw "thinkpad" is an allowable model.

I then looked at setupcon's config file-- it reads the keyboard type from /etc/default/console-setup, and specifically from the lines
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

I changed the first line to
XKBMODEL="thinkpad"

and now things seem to work much better. I'll know for sure, if the problem doesn't recur in the next few days.

---

