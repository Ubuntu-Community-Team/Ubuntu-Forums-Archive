---
title: "To help Logitech (MX310) owners w/their buttons..."
date: 2009-08-11
forum: Hardware
---

### Post by neologix on 2009-08-11
It took me a while to make this work, but when I did I jumped for joy! I'm running Jaunty Jackalope and if you have a Logitech mouse w/a button listed as "button 10" or higher in *xev* this is the thread for you!

First, visit the ["configuring logitech mice" thread]("http://ubuntuforums.org/showthread.php?t=65471") to configure your mouse and get your "Back" & "Forward" buttons working "properly" in Nautilus and such using *xvkbd* and *xbindkeys*. I'll wait...

Back? Okay! Now, if you came from Mac OS X like I did at one point, you might've mapped your Logitech button (normally used for an application switcher on Windows) to some Expose function; I mapped it to "Show all windows" which, if you've enabled compiz and installed the ccsm, can be found in ccsm's Window Management -> Scale. The command to "show all windows" is known as "initiate window picker" and you can set a screen area, keyboard combo, and/or mouse button combo to activate it.

The Logitech button is known as button 10 for me, so it's not normally in ccsm's standard dropdowns (it only shows 1-9 for me); instead, you must click on the pencil & paper icon of the mouse action for "initiate window picker" (ATTACHED SCREENSHOT 1) and in the resulting dialog box (ATTACHED SCREENSHOT 2), enter *Button10* and click OK. For more OSX-like behavior, toggle on "button bindings toggle scale mode." I also set a corner to do it, too. I tried setting a key combo in *~/.xbindkeysrc*, but it wouldn't work properly for me for some reason.

SO! In summary, for any compiz option you'd like to set to button 10 or higher and it doesn't appear in the standard dropdown for mouse actions, click the pencil & paper icon & type in *Button##*, where ## is the number of the button.

---

### Post by svenni on 2010-11-03
Thanks for the tip. It didn't work for me to use the pencil, however I was able to do the same thing by changing the settings directly in gconf-editor. The relevant settings for Scale is located in 
```
/apps/compiz/plugins/scale/allscreens/options/initiate_all_button
```
or
```
/apps/compiz/plugins/scale/allscreens/options/initiate_button
```

Setting the value for either of these to Button10 did the trick for my G500! :D Thanks again, I've been missing the option to use this button since I got the mouse.

---

