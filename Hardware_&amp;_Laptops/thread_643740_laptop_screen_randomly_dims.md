---
title: "laptop screen randomly dims"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by systemintheglitch on 2007-12-18
I have disabled all the places where this effect can be controlled.. Please, this is so annoying.

---

### Post by wharp on 2007-12-18
Could you be more specific about where exactly you've tried disabling it.

---

### Post by eldragon on 2007-12-18
most notebooks have this power saving feature of dimming the display when its not connected to ac... 

i would check if the power connector on the notebook isnt broken...

---

### Post by systemintheglitch on 2007-12-18
Thank you for the help!

The places where i have checked the setting are:
on the little battery icon down in the panel.> If you rightclick and say preferences or something..
I have disabled ALL the settings that would make the screen dim under ANY circumstances.. Such as when its idle for a while, when it's plugged in or not plugged in.. 

My computer plug is fine too. New computer.

---

### Post by systemintheglitch on 2007-12-18
The technical name for that program where i adjusted the settings is gnome-power-preferences

---

### Post by wharp on 2007-12-18
When you say randomly, is it really random? Or is it after a certain period of time?  It doesn't dim while you are working on it does it?

---

### Post by systemintheglitch on 2007-12-19
No not while i work on it.. 

But sometimes after only like 30 seconds.

I know when you have the option to dim when idle it should be a lot longer than 30 seconds..
AND that option is turned off on my system..

---

### Post by fdimmling on 2007-12-19
I have the same problem - dimming after very short idle time - on a Dell Inspiron 6400 I setup for a friend with Gutsy. You have to manually - by F keys - increase brightness again - quite annoying. Fortunately this friend told me she does very seldom need battery operation. 
On my own Aver Travelmate 4650 I do NOT have this problem. Brightness keeps stable all the time.
Anyway the problem is obviously insensitiv to all parameters you can set from the gnome-power-manager.

Friedrich

---

### Post by systemintheglitch on 2007-12-20
> **fdimmling said:**
> I have the same problem - dimming after very short idle time - on a Dell Inspiron 6400 I setup for a friend with Gutsy. You have to manually - by F keys - increase brightness again - quite annoying. Fortunately this friend told me she does very seldom need battery operation. 
On my own Aver Travelmate 4650 I do NOT have this problem. Brightness keeps stable all the time.
Anyway the problem is obviously insensitiv to all parameters you can set from the gnome-power-manager.

Friedrich

Thanks, even if you don't have a solution it's sometimes good to know someone else out there feels my pain! :)

---

### Post by kinobe on 2008-01-05
Yea I'm getting this too on my inspiron 1420 (not n, this came with Vista and a GeForce 8400M GS gfx card). It just dims out whenever it bloody feels like it (usually around 15secs of idle time, but sometimes while i'm in the middle of doing something too).

I have turned off the dimming feature and set the screen brightness to be 100% both on AC power and battery but no joy. If someone managed to fix this I'd be grateful to know how. Thanks.

---

### Post by spier on 2008-01-05
There is another place to set gnome power manager options:
 
Start Gconf-editor:
Alt-F2 > type gconf-editor> run 

Select apps menu > gnome-power-manager
 There are some options to try:
- dim-on-idle
- backlight  menu >  idle-...

Now, notebooks have very specific hardware that  have specific issues. Some options in some computer still don't work :(

---

### Post by ulisse on 2008-01-09
On a 6400 of a friend it seems that the issue was due to the ambient sensor (that on that laptop is not present at all...).
Disablling the option with gconf-editor solved the problem

---

