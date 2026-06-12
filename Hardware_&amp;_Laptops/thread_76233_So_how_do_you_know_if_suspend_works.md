---
title: "So how do you know if suspend works?"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by nehalem on 2005-10-14
I'm not sure if it works on my laptop?  How can I test this?  Command??

---

### Post by kvidell on 2005-10-14
You could always just try hitting the Fn+Something key combination for suspend... that works out of the box on my ThinkPad (FN+F4). It could possibly just be tapping the power button on other devices.

I'm not sure what the command is to send that to the board though :-\ Sorry.
- Kev

---

### Post by nehalem on 2005-10-14
Hmmm.  The function key combo doesn't work.  I do have the lid and it does more than in previous releases (brings me up to a log on screen) but I still don't know if it's suspending to ram (lights are still on, but not my toughpad).  It seems like there should be some uniform way to figure this out.

---

### Post by kvidell on 2005-10-14
hmmm... yea, I'm not sure.
In Hoary _nothing_ happened.. ever... now in breezy it's quite responsive to my ThinkPad's state(s).

If I shut the lid it kicks in the screensaver and locks it. If I hit the power button, it hibernates, if I do the suspend combo, it suspends, and if I unplug it the power management profile automatically changes.

I'm not sure how to do any of it though (set it up), as it was out of the box...
My fiance may have some insight in to it as he had this thinkpad doing most of this in Hoary as well.
- Kev

---

### Post by netsyd on 2005-10-15
[QUOTE=nehalem]Hmmm.  The function key combo doesn't work.  I do have the lid and it does more than in previous releases (brings me up to a log on screen) but I still don't know if it's suspending to ram (lights are still on, but not my toughpad).  It seems like there should be some uniform way to figure this out.[/QUOTE]

Generally all systems when they are in a "suspend to ram" state will have a flashing power light. They may slowly pulse or whatever, but for the most part they all  "go on - go off - go on etc."

Hibernation "suspend to disk" will generally act something like the following: 
1. your screen goes blank
2. your hard drive starts working it's butt off for about 10-20 seconds
3. your power light & hard drive light goes out and stays out and you can hear the system power itself off (fan spins down"

The problem with most systems is not the putting to sleep, but the waking up... 

Hope that helps...

---

### Post by Joe_lurker on 2005-10-15
Try apm -s from the console.  you can read the man page for more options.  You can also try sudo /etc/acpi/sleep.sh sleep if your computer supports acpi.

Joe

---

