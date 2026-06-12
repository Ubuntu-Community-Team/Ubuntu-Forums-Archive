---
title: "Need help! No ubuntu loading screen and.."
date: 2008-08-01
forum: General Help
---

### Post by Kromgol on 2008-08-01
Some black small things upper in the left corner, no this is not bugs or anything, not dead pixels either.

I recently installed the startup manager, and enabled 24-color depth for the screen, but now, the ubuntu loading screen will not show up (Black) but it will still boot, and then i got some weird black pixels up in the upper left corner. As i said, these is not dead pixels or anything, i just got it after i changed the setting, i also changed the boot timer to 3 seconds.. That did work, but changed back later.

Then i changed back to 8-bit, and that didn't seem to help either, it was still the same.. I'm getting really annoyed by them.. As they show up the one second, then disappears etc.

[img]http://data.fuskbugg.se/skalman01/-Skrmbild.png[/img]

I really, really want this solved, thank you.

Edit: I got an old fat 19" screen if that's important.. With a Nvidia 8500GT graphic card.

---

### Post by pastalavista on 2008-08-01
You might check the screen resolution setting in /etc/usplash.conf

```
sudo gedit /etc/usplash.conf
```

if it is wrong, lots of things can go wrong but especially really slow boot time.

---

### Post by Kromgol on 2008-08-01
I only found these two lines in the config file:
xres=
yres=

I do not know if there should be more, but anyway..

The resolutin was at 1280x1024 and my monitor doesn't support that, so i changed back to 640x480 and rebooted, didn't change so much..

More help is appreciated :p

---

### Post by Kromgol on 2008-08-01
Now i got it all working by updating initramfs! Seems like that is needed to apply the update in usplash.confg.

Anyway, no black dots or no ubuntu screen.

EDIT: Yes, the boot screen works, but when shutting down Ubuntu, the screen that comes up then, seems to have very low color depth in it.. Looks ugly.

Help?

---

### Post by pastalavista on 2008-08-01
If the monitor can only support 640x480 it would have to be very old. Try changing it to 800x600 or 1024x768. 

(edit: larger number in usplash.conf is the xres= smaller number is yres= )

---

### Post by Kromgol on 2008-08-03
> **pastalavista said:**
> If the monitor can only support 640x480 it would have to be very old. Try changing it to 800x600 or 1024x768. 

(edit: larger number in usplash.conf is the xres= smaller number is yres= )

I changed to 800x600.. But then the boot screen went to the right bottom corner.

Well, this monitor is very old. I think it's 8 years.

---

