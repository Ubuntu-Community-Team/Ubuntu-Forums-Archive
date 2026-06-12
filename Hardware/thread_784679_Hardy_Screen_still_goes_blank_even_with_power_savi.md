---
title: "Hardy: Screen still goes blank even with power saving set to 'Never'"
date: 2008-05-06
forum: Hardware
---

### Post by jimv on 2008-05-06
My laptop screen still goes blank after awhile when plugged in, even though I've set the Power Saving control panel to never blank the screen.  To add an even odder bit, if I move the mouse a few minutes after it goes blank, then the screen comes back up.  But if I wait about 20-30 minutes before moving the mouse, the screen doesn't come back on until I restart the X server.

Any ideas?

---

### Post by StaceyRVC on 2008-05-06
I thought I was the only one having this problem. I constantly have to keep restarting the laptop for it to become active again. I would love a solution to this as it's driving me a bit insane.

---

### Post by jimv on 2008-05-07
I think I may have found a solution.  I was googling around and found some guy who said to add these lines to your xorg.conf (back it up first
```

Section "ServerFlags"
	Option	"BlankTime"	"0"
	Option	"StandbyTime"	"0"
	Option	"SuspendTime"	"0"
	Option	"OffTime"	"0"
EndSection
```

If you already have options in that section, you can leave them in.  I didn't test it yesterday when I made the change, but I'll try to watch and see if the screen goes off today.

---

### Post by StaceyRVC on 2008-05-07
> **jimv said:**
> I think I may have found a solution.  I was googling around and found some guy who said to add these lines to your xorg.conf (back it up first
```

Section "ServerFlags"
	Option	"BlankTime"	"0"
	Option	"StandbyTime"	"0"
	Option	"SuspendTime"	"0"
	Option	"OffTime"	"0"
EndSection
```

If you already have options in that section, you can leave them in.  I didn't test it yesterday when I made the change, but I'll try to watch and see if the screen goes off today.
Thanks alot Jim, I just did this also.. I really hope it works!

---

### Post by StaceyRVC on 2008-05-11
Ok, so I fully tested this out this morning and after the screen goes "blank" I have NO way of "waking" it up to input my password. I have to ctrl-alt-backspace to get back into the system. I am almost at wits end with this :( anyone have another suggestion?

---

### Post by pablomme on 2008-05-27
Does it help if you type the following on the command line before playing video?

```
sudo /etc/init.d/laptop-mode stop
```

You can undo this afterwards with

```
sudo /etc/init.d/laptop-mode start
```

---

