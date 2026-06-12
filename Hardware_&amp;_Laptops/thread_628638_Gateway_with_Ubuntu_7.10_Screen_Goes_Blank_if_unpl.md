---
title: "Gateway with Ubuntu 7.10 Screen Goes Blank if unplugged"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by emergingtechnologies on 2007-12-01
My upgrade to 7.10 is going great except for this nuisance: I can't use the laptop without it being plugged in.  It works great if plugged in but when I unplug it, the screen goes blank.  When I plug it back in, the screen shows up again and everything is fine.

If I start it without having it plugged in, I will see all the startup screens before the login screen -- when I log in, it goes blank.

I have searched these forums up and down looking for something close -- I haven't seen it.

I would love some direction on this situation.

Thanks,
Chris

---

### Post by emergingtechnologies on 2007-12-02
Any ideas?

---

### Post by mbobb827 on 2008-03-24
I am having the same exact problem. Is thee any answer?

---

### Post by emergingtechnologies on 2008-03-25
This was not happening with 7.04 -- only started with 7.10 -- chances are good that it will be fixed with 8.04 -- only 30 some odd days...

It hasn't soured me on Ubuntu!

---

### Post by chilinski on 2008-03-25
I notice when I remove/install the ac power to my EEEPC that the screen brightness indicator comes on and that there's a definite difference in brightness between AC and battery. Perhaps something like this is happening related to power settings.

Of course, I could FOS and just leading you on a wild goose chase (unintentionally, by the way)  that will eventually say to yourself, "why the hell did I fall for that one?" But who knows?

---

### Post by coreyb42 on 2008-04-23
Managed to fix it on my Gateway, doing the following (while plugged in):
1. Go to System -> Preferences -> Power Management
2. Click the "On Battery Power" tab
3. Slide "Dim display brighness by" to 0% - tried 30% and it didn't work either, but 0% lets me unplug the computer and actually use it.

Also, on my Gateway, there's a function button for dimming the display, anyway, so you can do it manually.

Oh, and thanks, chilinski! Wouldn't have thought of it without you.

---

### Post by emergingtechnologies on 2008-04-24
Hardy fixed it for me...

---

