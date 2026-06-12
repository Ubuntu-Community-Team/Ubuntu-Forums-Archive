---
title: "Ubuntu 7.10: Xlib:  extension &quot;XFree86-DRI&quot; missing on display &quot;:1.0&quot;"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by mlivio on 2007-10-25
Hi,


Summary:
OS: Ubuntu 7.10
Graphic Card: ATI Mobility X300
ATI Restricted: drivers are installed
Server Xgl: installed and running
Compiz: working fine
Problem: 3D applications not running ( error ib:  extension "XFree86-DRI" missing on display ":1.0")


I recently installed Ubuntu 7.10 on my laptop and since then I have the following problem:

When starting googleearth I get thsi message, Xlib:  extension "XFree86-DRI" missing on display ":1.0" and googleearth doesn't start.
As I installed the Xgl server following the ubuntu help instructions, I tried this, DISPLAY=:0.0 googleearth, the 3D application starts but the window doesn't have borders.

Is there a way to use restricted ATI drivers with Xgl and have the window borders when running 3D application as above (ex.DISPLAY=:0.0 googleearth)  ?
I tried to find a fix or workoaround but none worked :-( !!!!!!


Thanks for helping,

Livio :-) !!!!!

---

### Post by mlivio on 2007-10-29
Hi,

am I the only one experiencing  this problem on Ubuntu 7.10 as I can't find any solution or workaround and the forum community neither?!?!?


Livio :-( !!!!

---

### Post by ajadams2 on 2007-10-29
I have an ATI FireGL v5250 and i get that error alot.  I don't have a solution but still searching.

---

### Post by cow_racer on 2007-10-29
you have to disable xgl.


Whenever I want to play game, I have to disable xgl, or I will get the problem you are getting.


when i have to play game, I disable xgl.
touch .config/xserver-xgl/disable

to enable.
rm .config/xserver-xgl/disable

---

### Post by mlivio on 2007-10-29
Hi,

thanks for helping.
I also recently found the touch workaround for disabling xgl and I also found the below workaround but I can't find a real solution, ATI drivers are real crap my other PC with Nvidia GPU works great !!!!!

Workaround;

- "sudo apt-get install kwin"     (this is the KDE windows manager)
- in a terminal type; "export DISPLAY=:0.0" and then "kwin&"
- now from the same terminal window you can launch you 3D application
- when you want to get back to your standard window manager, just close you 3D application and kill kwin

I know it's not very nice but at least you don't have to do "touch ~/.config/xserver-xgl/disable" and then "ctrl+alt+backspace" for restarting X11


Livio ;-) !!!!!

---

### Post by turbod33 on 2007-10-29
Is this really the only way to disable XGL? 

I have an ATi card, with fglrx and compiz running fine. Is this the only solution so far? 

DV

---

### Post by mlivio on 2007-10-31
Hi guys,

check this out (method 2), it might help but I didn't try it yet:


[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)


Livio :-) !!!!!

---

### Post by Raistlin355 on 2007-11-15
I just started to run "export DISPLAY=:0.0" before running any 3d apps works good, still have compiz running but whatever you launch from the window you did the export in it will run "on top" of you window manager and have no border :.(
Although this does work, I play Wow this way but a better solution needs to be found........

---

### Post by andresv on 2007-11-16
> **Raistlin355 said:**
> I just started to run "export DISPLAY=:0.0" before running any 3d apps works good, still have compiz running but whatever you launch from the window you did the export in it will run "on top" of you window manager and have no border :.(
Although this does work, I play Wow this way but a better solution needs to be found........

Thanks ... same problem, and same solution (:???:) here...

---

### Post by Raistlin355 on 2007-11-17
Ok got a little better way of doing it.  What I did was make a new account called "game" you can make this whatever you want then in the home directory of that account I made a folder and a file called "~/.config/xserver-xgl/disable" now there is nothing in the file so just make an empty file and call it disable.  So in the end on my comp is you look in "game"'s home directory you will see "/game/.config/xserver-xgl/disable" and this disable xgl on a per user basis, I have found this to be a better solution.

---

### Post by mlivio on 2007-11-18
Hi,


I finally manually installed ATI driver 8.42.3 (the latest one) and everything work fine without    
using xgl.
I then recommend all of you to install the ATI latest driver following the instructions at the below link:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)


P.S.
I just don't understand why this driver is not been included in Ubuntu restricted drivers instead of using and old ATI driver in restricted drivers, this should be update regularly.


Livio ;-) !!!!!

---

### Post by captainTK on 2007-12-29
> **mlivio said:**
> Hi,

thanks for helping.
I also recently found the touch workaround for disabling xgl and I also found the below workaround but I can't find a real solution, ATI drivers are real crap my other PC with Nvidia GPU works great !!!!!

Workaround;

- "sudo apt-get install kwin"     (this is the KDE windows manager)
- in a terminal type; "export DISPLAY=:0.0" and then "kwin&"
- now from the same terminal window you can launch you 3D application
- when you want to get back to your standard window manager, just close you 3D application and kill kwin

I know it's not very nice but at least you don't have to do "touch ~/.config/xserver-xgl/disable" and then "ctrl+alt+backspace" for restarting X11


Livio ;-) !!!!!

thanks for that workaround.
i have the same probs with ati-drivers. hopefully there is some solution for that prob.
i wrote a short shellscript which helped me for some 3d-games which suffered of poor performance (FretsOnFire, World of Padman).

**run.sh**
```

#!/bin/bash
export DISPLAY=:0.0
$*

```

cya

---

