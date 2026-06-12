---
title: "Dell XPS 1330M 2 video questions"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by xkaliburx on 2008-01-30
Here are the 2 things bothering me.

1. External video.  I have a Dell 22' EWP monitor connected, and it sets it up as a streched desktop.  I don't want this, I want to have my full desktop on that monitor and be able to close the laptop screen, right now when I do that, both the laptop display and monitor shut off.

2. Brightness.  If the laptop is running on battery, and I don't touch the machine for 60 seconds or so, it instantly goes 50/60% dim.  I then have to function brightness up, up, up to restore it.

Bios is set not to do anything so any help on either of the above is appreciated.

lr

---

### Post by drsaamah on 2008-02-05
I don't have an external monitor, but i have the same problem as you with screen brightness.  For me the brightness turns ALL THE WAY DOWN after variable periods of inactivity.  Sometimes a minute, sometimes 10 seconds.  And I need to use the function keys to turn it back up.
Has anybody else been having these problems with any Dells?

---

### Post by drsaamah on 2008-02-05
Scratch that!  Okay what ubuntu is doing (which it didn't use to do on my old inspiron...) is automatically adjust the brightness to the power management settings.  So if you go to system->preferences->power management, and adjust the "Set Display Brightness to: " that value is what the brightness will automatically adjust to.
So i suppose the question now is, how do we turn this feature off?  I don't want my screen brightness automatically adjusting to anything.

---

### Post by sgleo87 on 2008-02-05
just uncheck the "dim display when idle" in the power management. 
As for the external monitor: I have my external monitor for my laptop set up so it mirrors my laptop and I used the Twin View opton in the Nvidia settings. And I do not close the laptop lid, I just turn the laptop monitor off with a button on my laptop (FN key + one of the F buttons).

---

### Post by drsaamah on 2008-02-05
its been unchecked.  its not a 'dim' monitor thing.  now if its dimmed, and then left inactive, it will brighten up.  the problem is, it automatically adjusts to whatever the brightness setting is  set to (depending on adapter/battery).  i had gutsy on my ispiron and i dont remember it doing this...

---

### Post by drsaamah on 2008-02-12
HEY I THINK I FIXED IT!!
Alright my friend who just ditched Windows for Ubuntu :-) pointed out the most obvious fact in the world to me.  When I use the function keys to adjust my screen brightness I get a little brightness meter that pops up on my screen (kind of like the volume meter).  And I definitely didn't get that on my old laptop running Gutsy.  So SOMETHING on a software level is fighting with my BIOS over the brightness.  So I'm like "shyyy, what's the difference between this laptop and old one...?"  BOOM!  Nvidia, biatches.  SO here's the fix...
Pop open a terminal or use Alt+F2 and type in "nvidia-settings".  This will give you the Nvidia settings manager.  On the left side on the screen go to the menu titled "X Server XVideo Settings".  At the very top on the right side there's a check box labled "Sync to VBlank".  UNCHECK that mess.  Then quit the settings manager and you *should* be good.  I did it roughly an hour ago and I haven't had a problem yet.

---

### Post by xkaliburx on 2008-02-12
Damn, there ya go.  Ironically I used that damn menu daily at work to change from twin-view, can't close the laptop but it does black out so that's fine by me.  But switched over, pulled the plug and just waited... and waited... and like you said, sometimes it 10 secs, other times a bit longer, but looks like you found it ....

Good job .....  you have saved what is left of my sanity.  Wasn't a critical issue, but I am sure you realized ... annoying as all hell!

Tnx

---

### Post by drsaamah on 2008-02-21
actually i guess that didn't totally fix it... hehe. at least not for me.  BUT this time I found the solution for real (i swear!).  Its gnome thats messing with the screen brightness.  I guess maybe the Dell ubuntu comes with this option enabled by default or something.  So the REAL way to fix this problem is as follows:
   1)bust open a terminal and type in "gconf-editor'  You dont have to be a super user to run this.
   2)when the window opens, on the left side choose 'gnome-power-manager --> backlight
   3)on the right side on the backlight menu UNCHECK the box next to 'enable'.

And that's it.  I did this about a week ago and haven't had a problem yet.  Hope it works for everyone else!!

---

