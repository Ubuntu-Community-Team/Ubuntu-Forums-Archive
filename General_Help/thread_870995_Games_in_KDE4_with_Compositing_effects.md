---
title: "Games in KDE4 with Compositing effects"
date: 2008-07-26
forum: General Help
---

### Post by ProbablyX on 2008-07-26
Hello!

Does anyone have any fast, smooth, way of disabling compositing effects while playing games or using 3D apps in KDE4 - and put them back again while playing - like a script or plasmoid or so?

Thanks

---

### Post by Tim Sharitt on 2008-07-26
This is a script I have used in gnome. I would expect that replacing metacity with kwin (I think this is the standard kde window manager) would allow it to work with kde. I did not write the script, but I'll try to help with any problems I can.
Just run the script with the program as an argument.

```
#!/bin/bash
# runner
#
# Sun Oct 28 07:17:37 2007
# Copyright 2007 Enrique Schiel
# <ecschiel@yahoo.com.ar>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU Library General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301, USA

CHANGE=0

if ps -e | grep compiz; then
CHANGE=1
fi

if [ $CHANGE == 1 ]; then
printf "Disabling advanced desktop efects...\n"
/usr/bin/metacity --replace &

fi

printf "Running the game...\n"
$@ &
wait $!

if [ $CHANGE == 1 ]; then
printf "The game is finished. Restoring advanced desktop efects...\n"
/usr/bin/compiz --replace &
fi
```

---

### Post by overdrank on 2008-07-26
:) moved

---

### Post by ProbablyX on 2008-07-27
Thanks, but the effects are handled by KDE itself. That is theyre integrated into KDE's core. 
So if I will kwin, then the entire desktop will die wont it?

There is a way to disable them, that is by going into the System Settings, choosing Desktop and then "Desktop Effects" chosing "Activate desktop effects" there.

I was just wondering if there's a quick way for this.

Thanks :)

EDIT:
Here's an image of the dialog I found on the net:
[Pic]("http://bp0.blogger.com/_crimgO_xQv0/R5C0fEg-64I/AAAAAAAAAno/gMMQhuFiH6Y/s1600-h/desktop-effect.png")

As you see it's a tick box there saying Enable improved window management - this is a feature weaved into KWin

---

