---
title: "hangs on shutdown"
date: 2009-06-24
forum: Hardware
---

### Post by sdlynx on 2009-06-24
When I shutdown or restart my Ubuntu system (dual boot with Vista) on my HP dv5-1251nr laptop, it hangs after doing everything.  The splash screen shows up and the bar empties and that screen goes away.  Then there is a blinking underscore "_" at the top left corner of the screen and the computer does not shutdown.  Help?

---

### Post by recluce on 2009-06-24
> **sdlynx said:**
> When I shutdown or restart my Ubuntu system (dual boot with Vista) on my HP dv5-1251nr laptop, it hangs after doing everything.  The splash screen shows up and the bar empties and that screen goes away.  Then there is a blinking underscore "_" at the top left corner of the screen and the computer does not shutdown.  Help?

Let's see if we have the same issue: if you press "CTRL-ALT-DEL" at the time where you see the blinking underscore, do you get a message "Stopping all MD devices" followed by a regular shutdown?

---

### Post by sdlynx on 2009-06-24
> **recluce said:**
> Let's see if we have the same issue: if you press "CTRL-ALT-DEL" at the time where you see the blinking underscore, do you get a message "Stopping all MD devices" followed by a regular shutdown?

hmm.. actually yes I tried that and that's exactly what happened except I think it might have restarted instead of shutting down.  Also it made a bunch of noise on the speakers as it turned off.  The system also didn't hang when I shut down straight from the login screen.

---

### Post by cizin456 on 2009-06-24
The same problem happens to me. If i type "sudo shutdown -h 0" in terminal it works fine though. Although, i'm new to linux and don't really know what i'm doing by typing that, but i'm wondering if I can do something so that when i click shutdown or restart it runs that automatically. Any ideas? thanks.

cizin

---

### Post by lisati on 2009-06-24
I've seen discussions on the forums relating to similar problems, where there were a handful of different things causing the system to hang on shutdown. The particular workaround relevant to my machines related to the system hanging when trying to shut down wireless networking: I generally leave wireless switched off, and use a wired connection to avoid the system hang.

---

### Post by cizin456 on 2009-06-24
Is there a boot file we can modify to add the "-h 0" to shutdown and restart commands? what does this "-h 0" mean/do exactly? 

cizin

---

### Post by sdlynx on 2009-06-25
> **cizin456 said:**
> Is there a boot file we can modify to add the "-h 0" to shutdown and restart commands? what does this "-h 0" mean/do exactly? 

cizin

yeah I too would like to know

hmm wireless... maybe I'll turn it off before shutdown a couple of times and see.  The hanging only happens every 50% of the time also, so I'm not sure what triggers it.

---

### Post by recluce on 2009-06-29
Turns out that my problem is the "wireless hangup during shutdown" described in another thread. Turning off wireless before shutdown works.

---

### Post by sdlynx on 2009-06-29
ok thanks for the heads up I'll just do that

---

