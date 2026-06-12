---
title: "how do i enable proprietary ati-driver using command line only?"
date: 2008-08-29
forum: General Help
---

### Post by Mzwo on 2008-08-29
hi all,

i fear i may have done something stupid:
after installing google earth the programme wouldn't work properly, as in, the display kept flickering on and off (within the app). 
sooo - i thought it might be a good idea to deactivate the proprietary ati-driver (mobility Radeon 2400), to see if that helps. did that. restarted. and then:
screen went white. cube was still there, but everything is white. which means, i can't see what i'm doing and hence find it difficult to reactivate the graphics driver.

question: ho do i do this via the command line? because that still works. 

thanks,
Mzwo

---

### Post by Mzwo on 2008-08-29
ok, managed to reinstall the driver. next problem: screen resolution stuck at 800x600. display is detected as 1280x800 as it should be, but i can't select that resolution.

help?

ta,
Mzwo

---

### Post by eggdeng on 2008-08-29
> deactivate the proprietary ati-driver
You may well know this stuff already but it's not clear from your post, so just in case. If both drivers ati(free) & fglrx(proprietary) are installed, you can toggle between them by running
```
gksudo gedit /etc/X11/xorg.conf
``` and editing the line
```
Driver	"fglrx"
``` to
```
Driver	"ati"
```
Save, log out and log in again. So there is no need to uninstall / install anything. You can check which driver is specified in the config file by running
```
cat /etc/X11/xorg.conf | grep Driver
```
For Google Earth, you need to have fglrx. You can check if fglrx is loaded by running 
```
fglrxinfo
``` and
```
glxinfo
```
You should see your card identified and the line
```
direct rendering: Yes
```
First, make sure fglrx is running before you worry about the resolution problem. The reason you had these problems in the first place is because Google Earth is not compatible with Compiz. When you manage to get your system back to the state it was in, you can change Window Manager with
```
metacity --replace
```
to run Google Earth, and then
```
compiz --replace ccp
```
to revert to Compiz when you finish.

---

### Post by ugm6hr on 2008-08-29
> **Mzwo said:**
> ok, managed to reinstall the driver. next problem: screen resolution stuck at 800x600. display is detected as 1280x800 as it should be, but i can't select that resolution.

Try this:
```
sudo xrandr -s 1280x800
```

---

