---
title: "Maximize window on drag"
date: 2008-11-07
forum: General Help
---

### Post by Albert Fish on 2008-11-07
Hello guys. I'm fairly new to ubuntu and I was just wondering if it is possible to drag a window to the top of the screen and then have the window maximize itself?
I'm using ubuntu 8.10

--Albert Fish

---

### Post by Albert Fish on 2008-11-12
Bumpity bumpity bump.

---

### Post by rufus25 on 2009-06-28
I'm trying to achieve the same thing.

When I "pull" maximized windows away from the top, they un-maximize, but when I drag them to the top nothing happens.

---

### Post by thehud on 2009-11-27
*cough* bump *cough*... have either of you found a solution? That is... if you're still watching. I can even re-maximize a window that's been restored when dragged away from the top by dragging it back, so long as I haven't let go of the window. I'd really like  to drag any window to the top to maximize.

Anyone? Googles' not found me anything else yet (on the first few pages I check).

Ta, Hud.

Found nothing aside from this that is:
[[IMG]http://brainstorm.ubuntu.com/idea/21313/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/21313/)

---

### Post by rufus25 on 2009-11-30
I havn't found a solution. But I hope that now that windows comes with a really great automatic window placement management "aero snap", someone will find a way to get something like this working under Linux.

---

### Post by ed-koala on 2009-11-30
This sounds like something to add to the developers wishlist of features. I doubt you'll find an app that does this, probably needs to be part of X-serv or something like that.  Go to the Ubuntu developers page and ask for this to be added.  I'm sure it'll be a low priority though, so might take awhile to get it implemented unless it turns out to be a very simple thing to do.

---

### Post by patrick_the_fat on 2011-03-25
[Cited from [http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/]](http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/])

Open the Compiz Config Settings Manager (ALT+F2 ccsm, system > preferences > CompizConfig…, etc)
Select the “Commands” option.
In  ‘Command Line 0&#8242; paste: -
WIDTH=`xdpyinfo | grep ‘dimensions:’ | cut -f 2 -d ‘:’ | cut -f 1 -d ‘x’` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1


In ‘Command Line 1&#8242; paste: -
WIDTH=`xdpyinfo | grep ‘dimensions:’ | cut -f 2 -d ‘:’ | cut -f 1 -d ‘x’` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1


And in ‘Command Line 2&#8242; paste: -
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

It should now look something like this: -


Now choose the ‘Edge Bindings’ tab at the top and set the following: -

Run Command 0 – Set To Left
Run Command 1 – Set To Right
Run Command 2 – Set To Top
Click on the back button and go to ‘General options’.


Set the ‘Edge Trigger Delay’ to something around 400 – 500 by dragging the slider to the right.


Now all you have to do is drag a window to one of the specified sides and your window will automatically resize.

---

