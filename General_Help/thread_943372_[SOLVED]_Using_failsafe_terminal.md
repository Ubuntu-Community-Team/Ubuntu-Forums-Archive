---
title: "[SOLVED] Using failsafe terminal"
date: 2008-10-10
forum: General Help
---

### Post by DougieFresh4U on 2008-10-10
Intrepid
I get blank white screen after messing with screen resolution.
Was trying different ones and the last out of the 4 caused screen to come back blank white, no cursor either.
I can boot as far as Login & password screen.
Is there a code I can put in Failsafe terminal (from login window>sessions) to bring up 'Screen Resolution' that's in the 'Preference' menu?
I have tried to reconfigure x but it doesn't give me any thing to reconfigure or change.
I need to get into Screen resolution. I was using live CD but I do not know code or commands to fix via Live CD
Thanks

---

### Post by Pro-reason on 2008-10-10
Try “gnome-control-center”.

---

### Post by DougieFresh4U on 2008-10-10
> **Pro-reason said:**
> Try “gnome-control-center”.
Thanks very much for reply
How do I get 'gnome control center'?
All I get after login & password is a blank white screen. while in Login Screen I can change using Sessions to 'Failsafe Terminal' What shall I type in 'Failsafe Terminal?

---

### Post by DougieFresh4U on 2008-10-10
Got it!
I put 
```
sudo displayconfig-gtk
``` in the n'Failsafe Terminal'
and window popped that let me choose a lower resolution and rebooted and I had my machine back in order (relief)

---

