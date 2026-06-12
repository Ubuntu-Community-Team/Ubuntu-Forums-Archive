---
title: "ksynaptics touchpad applet does not work"
date: 2005-12-02
forum: General Help
---

### Post by eitan on 2005-12-02
hello,
  ever since i upgraded from ubuntu 5.04 to ubuntu 5.10, my ksynaptics
  touchpad control panel no longer works.  i have had to resort to installing
  a similar application: qsynaptics, which for some reason works without 
  any problems.

  to troubleshoot the problem, i launched ksynaptics from the command
  line;  when i attempt to "apply" my changes, i see the error message:
>>>
eitan@ubuntu:~$ kcmshell ksynaptics
kcmshell: load()
kcmshell: 0
kcmshell: save()
kcmshell: ERROR: Shared memory segment size mismatch
<<<

  so i get the error message, just not sure what to do about it.

thanks, / eitan

---

### Post by mlomker on 2005-12-02
You might want to file a Bugzilla if there isn't already an entry for the problem.

Does that applet just allow you to customize settings for the touchpad?  I'm curious because I have a touchpad but I don't need any additional software for it to work.

---

### Post by eitan on 2005-12-03
my main use for ksynaptics is to turn off the touchpad.
from the point of view of the touchpad, my notebook
computer has a lousy design:
  1. the touchpad is so large that when i type, part
  of my hand covers and activates the touchpad
  2. my touchpad was given its own scrollwheel-mechanism

so any time i attempt to type, my cursor goes flying everywhere
and other apps get activated and desktop files get thrown into
the trash.  so the first thing i do is disable the touchpad.

back to your question: ksynaptics appears to have fairly 
sophisticated controls to customize the behavior of the 
touchpad to one's liking.

my problem is that ksynaptics used to work with ubuntu 5.04.

---

### Post by mlomker on 2005-12-03
[QUOTE=eitan]my main use for ksynaptics is to turn off the touchpad.
[/QUOTE]

Have you tried removing the section from your xorg.conf file?

```

kdesu kwrite /etc/X11/xorg.conf

```

Delete the section similar to the following and then save it:

```

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

```

The next time that you restart KDE it should be disabled.

---

### Post by jounihat on 2005-12-03
I have this same problem with iBook G4. With KSynaptics I could get some cool features, like "Disable touchpad when typing", emulation of the second and third mouse button with the trackpad, emulation of scrolling with trackpad etc.

I hope this gets fixed soon, at the latest for Dapper.

---

### Post by GeneralZod on 2005-12-04
Bug report here:

[https://launchpad.net/distros/ubuntu/+source/ksynaptics/+bug/3406](https://launchpad.net/distros/ubuntu/+source/ksynaptics/+bug/3406)

---

### Post by eitan on 2005-12-06
although this is not directly related to my original post, i thought others might find it useful:

i spent a little time trying to understand qsynaptics and it basically does the same thing as the "synclient" command

that is, i added this startup program to my gnome session:
  synclient TouchpadOff=1

now after i login my touchpad is disabled, which in this case is what i wanted.

---

### Post by edrex on 2006-08-12
Wow, great tip eitan. I read through the synclient and synaptics (driver) manpages, and discovered TONS of interesting features. I'm going to turn off my Thinkpad's nipple so I'll actually start using the touchpad!

---

