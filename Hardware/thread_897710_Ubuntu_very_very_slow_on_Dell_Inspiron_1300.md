---
title: "Ubuntu very very slow on Dell Inspiron 1300"
date: 2008-08-22
forum: Hardware
---

### Post by tetristic on 2008-08-22
Hi-

I've just performed a fresh install of Ubuntu Hardy on my laptop. It's not a great spec: 1.40 gHz with 256MB RAM but windows worked fine on it so I was hoping Ubuntu would too...

However it is extremely slow, to the point where I think there must be a problem with something. At startup (after logging in) it takes several minutes for all the icons etc to appear and for the desktop to be usable. Starting up programs usually takes between 1 to 2 minutes. If I try to use more than one thing at once it takes even longer. It absolutely refuses to play any video eg youtube at anything other than about 1 fps.

A thread somewhere suggested running glxgears -info which I've done; it averages out about 500 fps.

I turned off all desktop effects, but this didn't help.

I also opened up the System Monitor. Roughly 80% of the RAM is being used at any one time; however the CPU usage is at a constant 100% even when I'm not running anything at all. And I've no idea why!

Any help is greatly appreciated. I'm a newcomer to Linux so might not be able to understand anything too technical. Thanks!

Russell

---

### Post by merlin051 on 2008-08-22
I'm using an 1300 also, but upgraded processor to 1.7ghz pentium 2mbL2cache and 768ram with glxgears i average 660fps

thought that might help you

---

### Post by tetristic on 2008-08-23
Not really I'm afraid because I can't afford to upgrade. To be honest i've tried runnning glxgears again and it averages nearer 600-650 than 500 - so running that doesn't seem to be a problem. Do you / did you find that everything ran at a snail's pace on your laptop before you upgraded and has the upgrade fixed it?

---

### Post by tetristic on 2008-08-23
OK, so on another thread I have been asking for help because my monitor backlight was dimmed, and one very helpful user suggested the following:

"try adding the module video to /etc/modprobe.d/blacklist

command: sudo gedit /etc/modprobe.d/blacklist

add to the file:

blacklist video

Make sure that you have a empty line at the bottum of the file "blacklist"

restart your computer."

Not only has this fixed my backlight it has also made everything else a lot faster as well, and I can now play videos fine! Programs still take quite a while to load but I can learn to live with that (unless anyone has any good suggestions...). Just thought I should post it here in case anyone with a similar problem comes across this thread.

---

### Post by kerry_s on 2008-08-23
> Programs still take quite a while to load but I can learn to live with that

you just need to trim gnome to work on your low 256mb ram, for example:
turn on low resource mode->
```
gconftool-2 --type bool --set \
/apps/metacity/general/reduced_resources true
```

i hope that's the right command, i usually just use the editor, cause i turn off a lot of stuff. see pic

anyway, continuing:
turn off animations, that's in the editor to
disable compiz & aiglx, in /etc/X11/xorg.conf, add to the bottom:

```
Section "ServerFlags"
Option  "AIGLX" "off"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection
```

use a low resource theme, bluecurve is the fastest, which is what i'm using.
replace gedit with leafpad
etc...

performance is up to you and how much your willing to give up for speed, for example i hear using openbox-gnome is suppose to be lighter, just openbox would be even lighter, it all depends on what you like, me i just choose to trim gnome and replace some of the slower parts with faster programs.

---

