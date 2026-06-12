---
title: "Wacom Intuos S / Inkscape 0.92 / Gnome Control Center Issue / 18.04"
date: 2019-01-19
forum: Hardware
---

### Post by rb100 on 2019-01-19
Had problems installing "[Wacom Intuos S]("https://www.wacom.com/de-de/products/pen-tablets/wacom-intuos")" under **Ubuntu** **18.04** (**Gnome** and [XWindow]("https://en.wikipedia.org/wiki/X_Window_System") System) using [Inkscape]("https://inkscape.org/de/") (0.92). The device has been recognized in "Gnome Control Center" by default. The testarea for handwriting worked well (including pressure sensitivity feature), but no other settings were possible. Inkscape does not offer pressure sensitivity feature of the Intuos. Additionally the center point of the pen and choosen Inkscape tools (e.g. calligraphy) had an _offset_ miles away from each other. This is as an indication of a wrong considered window input area.

Command "[FONT=courier new]libwacom-list-local-devices[/FONT]" suggest that only a generic Wacom device has been detected:

[FONT=courier new][Device]
Name=Wacom Serial Tablet WACf004
DeviceMatch=serial:0000:0000;
Class=ISDV4
Width=0
Height=0
IntegratedIn=Display;System;
Styli=0xfffff;0xffffe;...[/FONT]

I tried to update the "[FONT=courier new]libwacom[/FONT]" but there aren't newer files for ubuntu 18.04.

Finally solved the problems by:

[SIZE=3]**1.**[/SIZE] Install latest "tablet-data" and "svg" files attached below in this thread (or "[libwacom]("https://github.com/linuxwacom/libwacom/wiki")" project site). If using my files here you have to copy/rename them as follows:


[LIST]
[*]"[FONT=courier new]intuos-s-p3.tablet.txt[/FONT]" to directory: "[FONT=courier new]~/share/libwacom[/FONT]" and then rename this file as "[FONT=courier new]intuos-s-p3.tablet[/FONT]" 
[*]"[FONT=courier new]intuos-s-p3.svg.txt[/FONT]" to directory: "[FONT=courier new]~/share/libwacom/layouts[/FONT]" and then rename this file as "[FONT=courier new]intuos-s-p3.svg[/FONT]" 
[/LIST]
 
[SIZE=3]**2.**[/SIZE] After rebooting PC the "Gnome Control Center" should show functions for programming buttons and all the other settings being missed before. In my case Inkscape on the other hand listed the "Intuos" as an input device but unfortunately could not save nor change the "window input type" so that the above mentioned tooling _offset_ still was present. As this is obviously an Inkscape bug, all needed settings must be made manually like following:

[SIZE=3]**3. **[/SIZE]Close Inkscape and open file "[FONT=courier new]preferences.xml[/FONT]" located in "[FONT=courier new]~/.config/inkscape[/FONT]" with a text-editor

[SIZE=3]**4. **[/SIZE]Search for the responsible "[FONT=courier new]Wacom Intuos S[/FONT]" "[FONT=courier new]mode[/FONT]" parameters in the xml element "[FONT=courier new]<group id= "devices">[/FONT]" and change them from "[FONT=courier new]window[/FONT]" to "[FONT=courier new]screen[/FONT]" (see example below). Next save the file and open Inkscape. 

_Example:_

```
[FONT=courier new]
<group
     id="devices">
    <group
       id="P:Wacom Intuos S Pad pad"
       mode="[COLOR=#ff0000]screen[/COLOR]"
       axes="x;y;pressure;xtilt;ytilt;wheel".[/FONT]..[FONT=courier new]
[/FONT]
```
  
And maybe also:

```

[FONT=courier new]<group[/FONT]
[FONT=courier new]       id="P:Wacom Intuos S Pen stylus"
       mode="[COLOR=#ff0000]screen[/COLOR]"
       axes="x;y;pressure;xtilt;ytilt;wheel...."[/FONT]

```

Hope this will help other users!



[ATTACH]282241[/ATTACH][ATTACH]282240[/ATTACH]

---

