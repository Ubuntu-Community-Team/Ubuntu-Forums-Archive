---
title: "Suspend causes X to crash 50% of the time"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by Astro96 on 2006-12-15
Hi all,
I'm using Ubuntu 6.10 on a Dell laptop (the Latitude D620).  On Dapper suspend worked about half the time and crashed the entire computer the other half.  The upgrade from Dapper to Edgy fixed the complete crashing, so now suspend works great half the time and crashes X (I get the graphical login prompt) the other half of the time.

I have checked the X server logs and don't see any errors there (so maybe it isn't X that is crashing, but something else).  Where should I go from here to try to fix this problem?  Where is a good spot to start or logs to check?

Thanks,
Andy

---

### Post by antar on 2006-12-15
What do you mean by "crash"?

I'd get the problem where I'd get a blank screen upon opening my laptop lid after closing it or suspending it, but the way to fix that was Ctrl-Alt-F1, Ctrl-Alt-F7 (get to a text interface, then back to GNOME).

---

### Post by Astro96 on 2006-12-15
Sorry, I should have been more specific.  When it comes back correctly I am presented with the same password prompt that I get when it goes into screensaver.  Upon entering that password, I am presented with my desktop and whatever applications I had running when I put the system into suspend.

When it doesn't work I get the ubuntu login screen that looks like I just restarted my computer.  After entering my username and password I get my desktop without any of the applications I had open.

Thanks,
Andy

---

### Post by Astro96 on 2006-12-19
> **antar said:**
> What do you mean by "crash"?

I'd get the problem where I'd get a blank screen upon opening my laptop lid after closing it or suspending it, but the way to fix that was Ctrl-Alt-F1, Ctrl-Alt-F7 (get to a text interface, then back to GNOME).

I have noticed that occasionally if I go to the command line using Ctrl+Alt+F1 and then attempt to go back to the GUI using Ctrl+F7 I get similar symptoms to what happens after a failed suspend.  Perhaps these are related?  What kind of logs should I be checking?

Thanks,
Andy

---

### Post by Aspero on 2006-12-20
Every morning when I  get to the office my computer has crashed. I think it's related to the suspend mode as it doesn't do it during the day.

I tried the CTRL+ALT+F1 - CTRL+ALT+F7 but it locks up completely at that point and I have to hold the power button down to make it restart.

Is there a way to turn off suspend? I didn't see it in the power management options.

---

### Post by raul_ on 2006-12-20
Mine crashes 100% of the time, so you're better than me. are you sure there isn't an option? I'm checking in Gnome and it has a "Do Nothing" option. Doesn't that work?

---

