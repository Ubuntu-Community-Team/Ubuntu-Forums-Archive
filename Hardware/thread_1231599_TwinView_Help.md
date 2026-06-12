---
title: "TwinView Help"
date: 2009-08-04
forum: Hardware
---

### Post by arsin225 on 2009-08-04
I want CS to run on my monitor that does not run the X Server (If I'm using it correctly, the one with the start bar and whatnot)

It did it fine yesterday, today I booted up and it gave me some error so I had to reset my xconfig and then I made it like what I had before

[xconfig]("http://pastebin.com/f34ee891d")

But it wont open in the secondary monitor, when I open CS it says resolution (1440 x900) -- my main screen -- but I want it to be 1280 x 1024

Also it will only run at 16bit 

How can I make this work? Thanks

---

### Post by arsin225 on 2009-08-06
Anyone?

---

### Post by jocko on 2009-08-07
One way to do it is to set up your xorg.conf to run a separate screen on your other monitor instead of one extended screen on both monitors (TwinView).
The easiest way is to do it with nvidia-settings. In the X Server Display Configuration, click your second monitor, press the configure button and select the second option (Separate X Screens). Then click "save to X configuration file" and exit. Restart X and you should have a separate x screen running on your other display.
Then, to start any program on the second screen, just put "DISPLAY=:0.1" in front of the command.

Edit:
You can probably also use the "place Windows" plugin in compiz to force a specific window to always open on your second display if you want to keep your twinview setup. In ccsm (System-->Settings-->CompizConfig Settings Manager, which you get if you install the package compizconfig-settings-manager), click "window management" -->Place Windows.
In the second tab (Fixed window placement) you can add rules to force windows to open in a specific part of the screen.
I'm not exactly sure of the exact settings you need, but under "Windows with fixed positions", click "new". In the text box (positioned windows) you need to put a rule for recognizing the window you want to specify. You can do this by clicking the "+" sign next to the text box and then click the capture button and then the window you want to specify. I guess you will have to start cs first (if it normally starts fullscreen on your first monitor, you may need to run ccsm on your second monitor to be able to grab the window title).
If your primary monitor is 1280x1024 and your second display is to the right of the first, just change the "x" value to 1280 and make sure you activate the "keep in workarea" option.

---

### Post by arsin225 on 2009-08-07
When I make them as separate X Servers the second monitor goes blank

---

