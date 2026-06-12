---
title: "LCD goes off after user/ password screen"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by marisdembovskis on 2009-10-30
Hi.

Have Toshiba R500 and installed Ubuntu 9.10
When I bootup everything is fine, but when I enter login and paswd it goes on (logging me in) and [COLOR="Red"]screen goes off. [/COLOR]

In other words Backlight goes in, when pc is plugged to electricity, but backlight all the time is off, when working on battery!


attached 2 pictures.
Will appreciate any help!

Thank you!


[COLOR="Red"]
In battery mode:
# toshset -trmode off
transreflective mode: off
# toshset -trmode on

Backlight goes on and off. Works perfect!


in AC mode:
the same commands, 
**Backlight is on, so Lcd SCREEN IS DARK AND IMPOSSIBLE to see something!**


in AC mode till login:
Backlight is off.  So everything is fine
[/COLOR]

---

### Post by BbUiDgZ on 2009-10-30
> **marisdembovskis said:**
> Hi.

Have Toshiba R500 and installed Ubuntu 9,04. 
When I bootup everything is fine, but when I enter login and paswd it goes on (logging me in) and [COLOR="Red"]screen goes off. [/COLOR]

Any clues, why screen goes off? I can not work with that kind of screen. 

In the same time, when Im working on battery everything is just fine!
Also when im working on battery and plug in DC, screen is off. After taking of DC, screen is still off!

attached 2 pictures.
Will appreciate any help!

Thank you!

when you get to the login screen use a new (gnome) session to login.

---

### Post by marisdembovskis on 2009-10-30
Thank you BbUiDgZ for quick answer and giving idea!

When I get to login screen. On left bottom corner says Options -> Select Session - > Last, Gnome, Failsafe Gnome, Failsafe terminal. 

I choose Gnome. 
Is this what you meant?
If yes, the same happens. Screnn goes off. 


There is something in startup processes what messes up the system.


thank you for help

---

### Post by marisdembovskis on 2009-10-30
One more thing. 
Installed KDE environment. 
same thing, lcd goes off after login promt!
Attached last moment before screen went out!

---

### Post by mgmiller on 2009-10-30
After looking carefully at the images you provided, I don't think your screen is turning off.  I think your back lite is turning off, but the image is being displayed. 

See if there is a switch on your keyboard somewhere that controls the back lite or brightness.

There is something about setting the transreflective mode in Toshiba laptops to save power that is not working right in 9.04.
You can install a toshset utility and a simple script to control it.

See here for a how to:
[http://ubuntuforums.org/showthread.php?t=1192773](http://ubuntuforums.org/showthread.php?t=1192773)

Also, this may cease to be a problem with 9.10.  Did you try booting a live CD to see if the issue is fixed in Karmic?

---

### Post by marisdembovskis on 2009-10-30
Thanks for answer mgmiller!
Exactly it is related with stupid back light. 


it does not work, it opens new tab in firefox!

it did manually:

#!/bin/bash
trmode_status=$(gksudo "toshset -q *transreflective*")
echo $trmode_status | grep "on"
if [[ $? -eq 0 ]] ; then
	gksudo "toshset -trmode off"
else
	gksudo "toshset -trmode on"
fi



on battery mode, backlight went out and in. (twice executing command)
on DC mode, baclight was out. so very dark image, but impossible to see. 

toshset is already installed! 
apt-get update is done for all packages.



haven't tried 9.10 

 
Thank you guys for your knowledge and help!

---

### Post by marisdembovskis on 2009-10-30
gonna install 9.10 ubuntu and will give a feedback!

---

### Post by marisdembovskis on 2009-10-30
NOT SOLVED YET!
lcd works on battery the same as on  DC!


9.10 Amazing OS. Like it! Feel, look, performance!
Probably one of most best from 8.04, 8.10 and 9.04 



Thank you guys for help!
Thank you developers for sofware!

---

### Post by marisdembovskis on 2009-10-30
everything was working till first reboot. 

reality, install is fine. 
first bootup is fine. 
FROM second bootup is PROBLEM, backlight is off. LCD is dark, however there is an imgage shown and system is working!


Anybody knows, how to keep settings from first bootup?

---

### Post by marisdembovskis on 2009-10-30
How to keep 1.st boot settings???

---

### Post by marisdembovskis on 2009-10-31
I also tried to start everything from terminal.
it gave this message

(EE) Failed to load module "i810" (module does not exist, 0)


1. I attached Xorg.0.log
2. I atacched picture, from booting



Will appriciate any help!

---

### Post by mgmiller on 2009-10-31
Have you tried going into power manager, System > Preferences >Power Management  and setting all the screen blanking settings to never when both on AC and battery?  Same thing in the screen saver area, try setting never for the screen saver (untick "activate screen saver when computer is idle").

Failing this and the other things mentioned in the toshset utility, you may need to file a bug report.

---

### Post by marisdembovskis on 2009-10-31
Thanks for answer!

In battery mode till login and after login backlight is off:
# toshset -trmode off
transreflective mode: off
# toshset -trmode on

Backlight goes on and off. Works perfect!
(noticed that backlight goes on also on battery if I try to make brighter display over middle brightness using Fn F7 which make lighter LCD and then also in battery mode you can not get backlight off, unless you turn FN F6 to reduce brightness)


in AC mode:
the same commands,
Backlight is on, so Lcd SCREEN IS DARK AND IMPOSSIBLE to see something!
# toshset -trmode off
DOES NOT WORK!


in AC mode till login:
Backlight is off. So everything is fine. 


seems that it is a bug!
by the way is there a way, how to say in Power Management in AC section add Reduce Backlight Brightness. 
I don't have that option in AC section. But in Battery section I have ticked this option. 

Is there a way how to say for Power Management do exactly the same stuff, for Battery and AC state?




Sreensaver is off, everything seems to be done, but problem not solved yet!
It could also be conflict between toshset -trmode off and Power Management. Because naturally in Power Management you can not turn off backlight in AC mode. 




Thanks mgmiller for help!
Appreciate that!

---

### Post by marisdembovskis on 2009-10-31
stupid solution, but SOLVED!

Went to Power Management and AC Power mode tab. 
and SET DISPLAY BRIGHTNESS TO 35% and it works now on battery and AC
also worked with larger percents!
after getting worked once!


huh, at least it is some kind of solution, which should be fixed in updates!
nobody can now, that they should try change AC brightness %. :)


thanks to everybody for help!

---

### Post by marisdembovskis on 2009-10-31
one more thing!
in power management don't tick in when inactive after 5 minutes or so turn off monitor. 

everything for me was working, but after 5 minutes monitor went out and again was in backlight on mode. And could not make it off. 

1. I reboot in Battery mode.
2. in Power Management  -> ON AC -> Put display to sleep when inactive for NEVER!!!!!! & slide brightness to 40%. 
3. FN + F7 and then FN + F7 - take close look when backlight goes on (it did for me) and take back brigthness FN + F6 till level when backlight was off. 
Screen is dark. 

4. in terminal sudo su
 toshset -trmode on
 toshset -trmode off

make sure that:
transreflective mode: off


5. Plug Power cord in. Should be backlight off. 
In Power Management  -> ON AC -> can turn brightness to 100%. 


for me it seems problem not with toshet package, but with power management, because when in Power Managemenet -> On AC Power -> PUT DISPLAY TO SLEEP WHEN INACTIVE FOR X MINUTES, baclight goes in and even after reboot it is still on! And for me it took 3 days to get it working!

will send bug report!

---

### Post by mgmiller on 2009-11-01
One more place you can look is in Applications > System Tools > Configuration Editor.  If it's not there, keep reading, I give instructions for adding it your menus at the end of this post.

If it's not in your menus, then open a terminal and type:
```
gconf-editor
```

Once there, on the left side navigate to Apps > gnome-power-manager
Click on the little triangle to the left of gnome-power-manager to expand its drop down list and then click on "backlight".

On the right side of the screen, you will see various options for brightness and dimming on ac or battery, etc.

You can click them to change values and to turn on and off, etc.

These changes normally take effect immediately.

If you find this is a handy spot for you to get to often, then in the top of the gconf editor screen, click on "Bookmarks" and then "Add Bookmark"

Now every time you run the gconf editor, you can get to this area easily from the Bookmarks drop down in the top of the window.

To enable the gconf editor in your regula menu list, right click Applications in the top panel and then click "Edit Menus".

On the left side, click on "System Tools"

on the right side you will see a list of the items avaialbe.  Put a check mark next to "Configuration Editor".

Close the menu editor.  

If the item does not appear in Applications > System Tools, just log off and back on and it will be there.

---

