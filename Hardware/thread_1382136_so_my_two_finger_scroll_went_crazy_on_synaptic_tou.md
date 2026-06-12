---
title: "so my two finger scroll went crazy on synaptic touchpad...."
date: 2010-01-15
forum: Hardware
---

### Post by v1nsai on 2010-01-15
My two finger scroll as been working perfectly fine, until suddenly it wasn't.  When I try to use it it goes berserk and jumps all over the screen clicking randomly.  I thought maybe this was a ubuntu problem, so I booted into Fedora where it was working perfectly fine....same problem.  Is anyone else having this problem?  I really hope it's a GNOME problem and not my mouse having a problem :(  Everything else works perfectly fine and its a very new computer.

If anyone else is having this problem please let me know, it will at least make me feel better.....

---

### Post by n0dix on 2010-01-16
I really think is yout mouse. If you test it in two differents distros and get the same problem i think is the mouse :(

---

### Post by pi/roman on 2010-01-16
You can troubleshoot the problem with synclient.

Type "synclient -l" to bring up a list of options and values.  These can be changed by typing "synclient option=value".  Descriptions of the options can be found by typing "man synaptics".  Changes by synclient will be effective immediately but will only last for the current session so after you find the solution you need to implement it through HAL or xorg.

---

### Post by v1nsai on 2010-01-17
I'm not willing to give up on the mouse as dead yet, thanks for the troubleshooting tips.  I used a tutorial I found after some quick googling to set all the values for synaptic and it worked, but the fact still remains that it was working fine and then stopped so I'm a little worried.  Since no one else is having this problem it's probably something on my machine.

---

### Post by Capirex on 2011-02-24
I dont know if this will let you feel better, but i have the same problem.

Acer Timelinex 4820, Ubuntu 10.10, SynPS/2 Synaptics TouchPad.

I tryied few things: synclient options, on terminal or in the file */usr/share/X11/xorg.conf.d/50-synaptics.conf*, a script at startup with some synclient commands, some applications from synaptic.

No way, it sometimes behave right, sometimes not, and seem not to depend on what i do. Often it is crazy from startup, but sometimes it begins randomly.

Suggestions? Thanks.

Oh, now i cant use *synclient -m*, but, i dont remember how, i did, and i saw a lot of:

button 6 press
button 6 release
button 7 press
button 7 release
...

maybe also 4-5 i dont remember. Can this help?


Edit: maybe this will let u feel better. I have windows too on this machine and till now i never had problems.

---

### Post by v1nsai on 2011-02-24
Oh hell I forgot I started this thread.  I figured out the problem.  Booting into Windows for a while then back into any Linux distro always makes my multitouch go insane.  Rebooting right away doesn't always fix it, but ignoring it for a while then rebooting makes it go back to normal.  Everything is fine until the next time I use Windows.  Such is the mess of crazy code that is Windows.

---

### Post by tgalati4 on 2011-02-24
That problem goes away in time when you stop using Windows completely.

---

### Post by Capirex on 2011-03-03
I just used windows to set it up because this is my new notebook.
I'm not using it anymore and i have no problems. Thanks.
Let's see what happens when i use it again.

I solved another problem (finger1 down, f2 down, f1 up moves cursor) with [_[COLOR="Blue"]this[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/comments/116"), maybe it can help. Bye

---

