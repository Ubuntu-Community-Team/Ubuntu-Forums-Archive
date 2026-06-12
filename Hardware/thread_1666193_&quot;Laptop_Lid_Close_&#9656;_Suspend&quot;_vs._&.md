---
title: "&quot;Laptop Lid Close &#9656; Suspend&quot; vs. &quot;System &#9656; Shut Down &#9656; Suspend&quot;"
date: 2011-01-13
forum: Hardware
---

### Post by dli8ilb on 2011-01-13
hi.  i have been trying to figure this out for **hours** now..

using 9.10 Karmic.  i have set in the gnome-power-preferences to suspend when laptop lid is closed.

what i'm trying to find out is:

1) what script/command is called when "System &#9656; Shut Down &#9656; Suspend" is clicked?
2) what script/command is called when the laptop lid is closed?
3) how can i set it to when the lid is closed, the same script/command that is called when suspending from the menu is used??

i ask because sometimes during my session, i use the command "xrandr --output VGA1 --off" to turn off the TV that is connected to the laptop with a VGA cable.  when i close the lid to suspend, the TV turns on and off again..and when the lid is opened, the screens are both black!

however, when i click "System &#9656; Shut Down &#9656; Suspend" everything works perfectly, the TV does not turn on when suspended/resumed.

please help i've tried so many ways to get this to work, but i'm afraid i'll ruin the TV if i keep powering on and off like this while testing.

---

### Post by dli8ilb on 2011-01-14
bump.  i'm pulling hair trying to figure this out!

can a moderator please move this thread to the General Help section?
maybe i should have put it there in the first place, sorry. :oops:

---

### Post by dli8ilb on 2011-01-14
sorry for multi-posting, there was some sort of timeout error (502 i think it was)

---

### Post by Garthhh on 2011-01-14
> **dli8ilb said:**
> hi. i have been trying to figure this out for **hours** now..
 
using 9.10 Karmic. i have set in the gnome-power-preferences to suspend when laptop lid is closed.
 
what i'm trying to find out is:
 
1) what script/command is called when "System &#9656; Shut Down &#9656; Suspend" is clicked?
2) what script/command is called when the laptop lid is closed?
3) how can i set it to when the lid is closed, the same script/command that is called when suspending from the menu is used??
 
i ask because sometimes during my session, i use the command "xrandr --output VGA1 --off" to turn off the TV that is connected to the laptop with a VGA cable. when i close the lid to suspend, the TV turns on and off again..and when the lid is opened, the screens are both black!
 
however, when i click "System &#9656; Shut Down &#9656; Suspend" everything works perfectly, the TV does not turn on when suspended/resumed.
 
please help i've tried so many ways to get this to work, but i'm afraid i'll ruin the TV if i keep powering on and off like this while testing.
 
What happens when you choose the Blank Screen when closing the lid power management option?

---

### Post by dli8ilb on 2011-01-14
> **Garthhh said:**
> What happens when you choose the Blank Screen when closing the lid power management option?

hi Garthhh.  thanks for taking the time to reply.   when i choose Blank Screen in power management options, this is what happens:

1)  if the TV is **OFF** when the lid is closed, the TV comes on with a black screen, and only the cursor is visible.  when i then open the lid, the TV turns back off.  strange behavior..

2) if the TV is **ON** when the lid is closed, the TV shuts off properly.  when i then open the lid, the TV turns on as expected.

---

### Post by Garthhh on 2011-01-14
So  you close the notebook when the tv is on the TV actually goes off, or just goes to sleep?
what is the behavior of the tv when using other inputs & they are powered down or removed? what kind of tv/monitor is it?


Personally I found 9.10 to be a little buggy, 10.10 seems pretty good & allows all the 3rd party codecs to be loaded at install, 10.04 is ok but required a certain amount of mucking around to get things to work

---

### Post by dli8ilb on 2011-01-14
> **Garthhh said:**
> So  you close the notebook when the tv is on the TV actually goes off, or just goes to sleep?
what is the behavior of the tv when using other inputs & they are powered down or removed? what kind of tv/monitor is it?

Personally I found 9.10 to be a little buggy, 10.10 seems pretty good & allows all the 3rd party codecs to be loaded at install, 10.04 is ok but required a certain amount of mucking around to get things to work

i think it actually just goes to sleep (sorry, i misspoke).  unfortunately, i can't test with any other input except the VGA since this laptop only has VGA out.

and yes i agree Karmic has it's problems, but until now i've managed to overcome all but this one :-k

back to my original issue:

> 1) what script/command is called when "System &#9656; Shut Down &#9656; Suspend" is clicked?
2) what script/command is called when the laptop lid is closed?
3) how can i set it to when the lid is closed, the same script/command that is called when suspending from the menu is used??
ok, after many more hours searching, i think i figured out question 1..because running this command:
> dbus-send --print-reply --system --dest=org.freedesktop.DeviceKit.Power /org/freedesktop/DeviceKit/Power org.freedesktop.DeviceKit.Power.Suspend
suspends the computer/TV gracefully just like it does when "System &#9656; Shut Down &#9656; Suspend" is clicked.

now i just need to find a way to run that command when the laptop lid is closed...any ideas?

---

### Post by Garthhh on 2011-01-14
> **dli8ilb said:**
> i think it actually just goes to sleep (sorry, i misspoke).  unfortunately, i can't test with any other input except the VGA since this laptop only has VGA out.

and yes i agree Karmic has it's problems, but until now i've managed to overcome all but this one :-k

back to my original issue:



heeeeeelp meh please!

If the tv is just going to sleep & waking up it won't be a problem for the tv

I was suggesting exploring the tv set up menus or is your computer the only possible input?

---

### Post by dli8ilb on 2011-01-14
> **Garthhh said:**
> If the tv is just going to sleep & waking up it won't be a problem for the tv

I was suggesting exploring the tv set up menus or is your computer the only possible input?

the TV doesn't seem to be the issue here.  i just would like to know:

> 3) how can i set it to when the lid is closed, the same script/command that is called when suspending from the menu is used??

because suspending from the menu (or running the aforementioned dbus-send command) makes it all work the way it's supposed to, whereas closing and opening the lid causes undesirable behavior.

see, if we take the TV out of the equation, the question still stands on it's own.  that's why i asked if moderator can move this to the General Help forum, which is where i'm now pretty sure it belongs.

---

