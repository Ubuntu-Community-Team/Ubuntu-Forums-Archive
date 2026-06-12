---
title: "Mouse controls reversed for users"
date: 2008-09-04
forum: Hardware
---

### Post by nym.null on 2008-09-04
I haven't seen this in any forums; I hope someone may be able to help with some guidance.

With the simplest of xorg.conf settings, I find that the mouse directional controls are reversed for different users on this particular machine. "User1" (me) gets different results from the other two users on this installation.

Left/middle/right click are unaffected but scrolling and paging are opposite for two users.
(Left/Right tilt is available on the mouse, but not working in these scenarios.)
Running Ubuntu 8.04; currently using a MS mouse, but hardware seems to make no difference.

xorg.conf is as follows:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option 		"ButtonMapping" 	"1 2 3 6 7 8 9"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

With these option settings... 
[INDENT]Option 	"ButtonMapping" 	"1 2 3 6 7 8 9"
Option	"ZAxisMapping"		"4 5"[/INDENT]

... User2 and User3 seem to have everything OK:

**Results:**
```
Mouse Action:	User1 Sees:	User2/User3 Sees:
scroll fwd/dn	right scroll	forward/down scroll
scroll bkwd/up	left scroll	back/up scroll
L button	page up		scroll left
R button	page down	scroll right
```

If I change Zaxis mapping to ... 
[INDENT]Option 	"ButtonMapping" 	"1 2 3 4 5 8 9"
Option	"ZAxisMapping"		"6 7"[/INDENT]

... these results listed above are exchanged: User1 gets the result listed for User2/3, and User2/3 gets the result listed for User1.

I am the only one with Sudo, so I know that no one else has made any changes.  In previous Ubuntu releases on this machine I have toyed with xvkbd and xbindkeys, but they are confirmed **not** to be installed.

I thought xorg.conf was supposed to serve up the same results for all users?

Thanks for reading and replying.

---

### Post by nym.null on 2008-10-09
> **nym.null said:**
> 
With the simplest of xorg.conf settings, I find that the mouse directional controls are reversed for different users on this particular machine. "User1" (me) gets different results from the other two users on this installation.
[...]

I thought xorg.conf was supposed to serve up the same results for all users?


Has no one ever seen this situation before?

---

### Post by nym.null on 2009-02-17
Four months later... Solved:

```

nym@indigo:~/.config/autostart$ ls -lh
total 28K
-rwx------ 1 nym nym  1.6K 2007-11-03 00:59 bluetooth-applet.desktop
-rwx------ 1 nym root  139 2007-06-18 22:29 evolution-alarm-notify.desktop
-rwx------ 1 nym nym   148 2007-09-02 18:02 firestarter.desktop
-rwx------ 1 nym nym   187 2007-09-04 13:42 for-2.desktop
-rwx------ 1 nym nym   125 2007-09-04 13:42 for.desktop
-rwx------ 1 nym root  109 2007-06-18 22:29 gshared.desktop
-rwx------ 1 nym root  110 2007-06-18 22:29 mouse.desktop
-rwx------ 1 nym nym   400 2007-09-02 18:03 trackerd.desktop

```

Three of these files were listed in **Nautilus** as **"No name"**:
"evolution-alarm-notify.desktop"
"gshared.desktop"
**"mouse.desktop"**

Deleting "mouse.desktop" and restarting GNOME solved the problem for me and did not impact the other users.

Contents of "mouse.desktop":
```

[Desktop Entry]
Name=No name
Encoding=UTF-8
Version=1.0
Exec=/home/login/mouse
X-GNOME-Autostart-enabled=true

```

So the mystery becomes "where did this file originally come from?"
And "why has no one ever seen this problem before or since?"

---

