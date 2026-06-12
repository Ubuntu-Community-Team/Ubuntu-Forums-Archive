---
title: "screen is blinking when only when i play game's"
date: 2008-09-11
forum: General Help
---

### Post by karantan on 2008-09-11
hi

i have a problem with my screen because its blinking when i play openarena or any other game. i tried to configured xorg.conf but i had no luck with that.

my hardware:
monitor: neovo F-419
graphic card: ATI Radeon X1300

Ubuntu 8.04 (hardy)

xorg.conf:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"si"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	ModelName   "F-419"
#	HorizSync   24-80
#	VertRefresh 49-75
#	Option      "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

as you see i have tried to set HorizSync and VertRefresh but it doesnt work. so if you have any ideas i'll be very grateful.

best karantan

---

### Post by karantan on 2008-09-14
[http://img508.imageshack.us/my.php?image=screenshottx1.png]("http://img508.imageshack.us/my.php?image=screenshottx1.png")

here is a screenshot

---

### Post by Shazaam on 2008-09-14
Do you have compiz running when you play games? If you do, turn Compiz off and try running the game(s) again.
You can install fusion-icon (sits in your tray) that allows quick access to turning compiz on and off. Make sure you have the Universe repo enabled in your sources list.

---

### Post by kk0sse54 on 2008-09-14
Are you running compiz? If so try disabling it for a few minutes  and switch to metacity and try to play your game

---

### Post by karantan on 2008-09-15
i do not have compiz...

---

### Post by karantan on 2008-09-20
now i know why my screen "blinks" when im playing games. its because my graphic card does not have 3D acceleration support.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) (i have x1300)

so much about linux compatibility and ready 4 desktop...

---

