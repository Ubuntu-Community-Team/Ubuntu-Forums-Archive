---
title: "[SOLVED] Screwed my X11/xorg.conf (newb^^) nVidia"
date: 2008-09-20
forum: General Help
---

### Post by Interpreter on 2008-09-20
Hi there, I've been using ubuntu since tuesday, was a XP user before.

I just tried enabling my Logitech MX510 thumb buttons and since I didn't even know what a xorg.conf file is I didn't back it up (mind you I don't even know how to go about that...) in the first place.
I had installed and configured my nVidia geforce 7600GT before, which was working fine at 1024x768@85Hz.

In the process of trying to enable these mouse buttons I somehow changed something to

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

...which doesnt have anything to do with graphics right?
Anyway, after saving that file I was told to restart/logout+login in order to allow X11 to read it's new config file and make use of it. I did the latter (logout) but instead of sending me back to a login screen, the resolution suddenly changed and I was told that my graphics card couldn't be detected and from then on everything is borked and fubar'd.

Finding myself being forced to use 640x480 without acceleration by my card, even posting here is a mess, since the lack of a detected graphics card does not seem to be the only issue.
It almost goes without saying that my attempt at bringing the thumb buttons to life also failed.
The worst thing though is that I cant make proper use of the menues, for when I leftclick on certain buttons, that results in making my mouse curser jump to some different position or even switching between various desktop, rather than calling a defined action.

So yeah I'm "nu to this", loving it to bits, but I realy didn't expect to run into major difficulties that go as far as to affect graphics and such when you're only trying to activate some standard buttons on a mouse...
doh
I've learned that lesson now, please don't give me the finger for that, to me thats just illogic -.-

The question: how can I change it back to using my card at 1024x768@85hz.

---

### Post by PurposeOfReason on 2008-09-20
You could run the command 'sudo nvidia-xconfig' to get it all working again.

---

### Post by Interpreter on 2008-09-20
Hm
....hmmm
thanks but that didnt change anything ((.
Rebooted of course...just in case..

---

### Post by Interpreter on 2008-09-20
But this one did it all ))

```
sudo displayconfig-gtk
```

---

