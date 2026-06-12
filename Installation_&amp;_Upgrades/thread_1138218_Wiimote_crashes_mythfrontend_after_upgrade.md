---
title: "Wiimote crashes mythfrontend after upgrade"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Triptol on 2009-04-26
Before I upgraded to Jaunty I had a working Mythbuntu installation with Wiimote control using cwiid (wminput).

After the upgrade every button click on the wiimote crashes the mythfrontend.

I have checked the wminput settings with wmgui and everything seems fine. 

So I started mythfrontend with the following options:
```
mythfrontend --verbose all
```
This is what I get as soon as I push a button on the wiimote:
```
mythfrontend.real: Fatal IO error: client killed
2009-04-26 13:38:54.280 MythSocket: readyread thread exit
```
I have no clue what my next steps could be. Ideas are appreciated!

My /etc/cwiid/wminput/buttons
```
#buttons

#Wiimote.A              = BTN_LEFT
Wiimote.A               = KEY_ENTER
#Wiimote.B              = BTN_RIGHT
Wiimote.B               = KEY_ESC
Wiimote.Up              = KEY_UP
Wiimote.Down            = KEY_DOWN
Wiimote.Left            = KEY_LEFT
Wiimote.Right           = KEY_RIGHT
Wiimote.Minus           = KEY_LEFTBRACE
Wiimote.Plus            = KEY_RIGHTBRACE
Wiimote.Home            = KEY_Y
#Wiimote.1              = KEY_PROG1
Wiimote.1               = KEY_M
#Wiimote.2              = KEY_PROG2
Wiimote.2               = KEY_I

#Nunchuk.C              = BTN_LEFT
#Nunchuk.Z              = BTN_RIGHT

#Classic.Up             = KEY_UP
#Classic.Down   = KEY_DOWN
#Classic.Left   = KEY_LEFT
#Classic.Right  = KEY_RIGHT
#Classic.Minus  = KEY_BACK
#Classic.Plus   = KEY_FORWARD
#Classic.Home   = KEY_HOME
#Classic.A              = BTN_LEFT
#Classic.B              = BTN_RIGHT
#Classic.X              =
#Classic.Y              =
#Classic.ZL             =
#Classic.ZR             =
#Classic.L              =
#Classic.R              =
```

---

### Post by Triptol on 2009-04-27
Nobody?

I know, I know, it is a shameless bump, but I really don't know what to do next.

---

### Post by Triptol on 2009-04-27
I don# think I posted this one correctly here, so I opened a new thread here: [http://ubuntuforums.org/showthread.php?p=7162402]("http://ubuntuforums.org/showthread.php?p=7162402").

Please post any comments in the new thread!

---

