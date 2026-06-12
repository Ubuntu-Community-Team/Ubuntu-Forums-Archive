---
title: "Razer deathadder 3500DPI"
date: 2012-03-24
forum: Hardware
---

### Post by Gr33nL34f on 2012-03-24
Can someone run me down on how to maybe lower the sensitivity for this mouse? its really fast, kind of hard to control and im a ubuntu noob so i dont know how to mess with commands. Thanks for any help its much appreciated. :confused:

---

### Post by cosmic_cow on 2012-11-19
Hopefully, you've figured this out by now; if not, here was my solution.
Open up your favorite text editor. Paste these contents in and save the file as [whateverYouWantToNameIt].sh (I called mine fixMouse.sh...I recommend putting it in either your home directory or on the desktop):

```

#!/bin/sh

mouse=` xinput | grep DeathAdder | awk '{print $6}' | awk 'BEGIN {FS="=";} {print $2}'`
xinput --set-prop $mouse "Device Accel Constant Deceleration" 5
xinput --set-prop $mouse "Device Accel Velocity Scaling" 1

```

Then either go into your file browser, right click, go to properties, go to the Permissions tab, and make sure it's executable, or open up a terminal, go to the directory the script is in, and run:

```

chmod 777 fixMouse.sh

``` 

where 'fixMouse' is whatever name you gave it. 

If you want it to run at every boot, make sure it's included under Startup Applications (it's under the gear menu on Gnome Shell, don't know for sure about other ones). Otherwise, you can just run that script manually and it will give you a reasonable sensitivity for your mouse. If you want it faster, you can increase the constants there (the 5 and the 1 at the end of the 'xinput' lines).
Hope this helps.

---

