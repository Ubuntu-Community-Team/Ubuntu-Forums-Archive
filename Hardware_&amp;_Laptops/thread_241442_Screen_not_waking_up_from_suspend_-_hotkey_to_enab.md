---
title: "Screen not waking up from suspend - hotkey to enable/turn on screen?"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by stiankarlsen on 2006-08-22
When I suspend my laptop, the screen refuses to turn back on when i try getting the laptop out of suspensiong... a very common problem, i've tried pretty much all i can think of, and have found on the forums...

However - a buddy of mine had the same problem on his laptop, only he was running windows xp, so what he did was to create a hotkey/key combination on the keyboard, that would enable/turn on the laptop screen when pressed, this solved the problem for him. And so I was wondering if there would be any possible way to create a hotkey that could enable the laptop screen, if possible this idea might work? I mean, if the rest of the computer is running normally, and only the screen is off....?

This might have been a stupid idea, since I have NO clue if its possible to do this in linux, but, well, i figured it might be possible?

---

### Post by mikeflys1 on 2006-08-22
I dont have any advice but im actually having the same problem.

---

### Post by m83 on 2006-08-22
I have an IBM Thinkpad T23 laptop and after I wake the laptop from suspend my screen is black also. Sometimes it comes out from suspend ok, the screen is enabled, but most of the time the screen is black when resuming from suspend.

When the screen comes out black I found out that pressing the key combination that cycles between LCD and the external CRT monitor brings back the screen. Basicly I cycle between LCD and CRT until the LCD comes back to life  (usualy it takes only a cycle).

---

### Post by stiankarlsen on 2006-08-24
But there must be a way to set a custom hotkey, a lot of people including me are having a hard time getting the FN keys to work...

---

### Post by yopnono on 2006-08-24
Well I have the same on my DELL D610 Intel graphic.
And it did resume from suspend up to 24h after that I must of the time need to hardreboot. Anyhow have tried this and so far so good, knock on wood.

[http://ubuntuforums.org/showpost.php?p=1178889&postcount=12](http://ubuntuforums.org/showpost.php?p=1178889&postcount=12)
and I also whitelisted the graphic module i810 in my case.

Also here is a script a tried to suspend, it works have not tried it much.
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)

---

### Post by jonlink on 2007-06-21
> **m83 said:**
> When the screen comes out black I found out that pressing the key combination that cycles between LCD and the external CRT monitor brings back the screen.
What is that key combination?

I am having this problem with my desktop monitor.  The interesting this is that it did something similar at start-- the screen would go black once Ubuntu got to the GUI.  To fix that I added 

```
	Option "MonitorLayout" "LVDS,Auto"
``` to the "Device" section in the xorg.conf file.  I wonder if there is a similar solution since it seems like the problem is just that Ubuntu is trying to use an analog monitor instead of the digital (dvi).

---

### Post by jonlink on 2007-06-27
Anyone?

---

