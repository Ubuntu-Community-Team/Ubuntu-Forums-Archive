---
title: "HELP!!! System restarts instead of shutting down!!!"
date: 2008-12-01
forum: General Help
---

### Post by dirac14 on 2008-12-01
Hello there!  I recently bought a new Toshiba Satellite A300D laptop (with amd athlon x2 64)and run Ubuntu 8.10(32bit) on it. My problem is that every time i click on the icon to shut down my laptop, it proceeds to all the normal functions in order to restart! Sometimes though, it does normally shut down without anything different from the above done by me. 
Is there any idea what should i do to fix that irritating problem??I am relatively new in ubuntu so please forgive my ignorance.
Thank you all in advance!

---

### Post by dirac14 on 2008-12-03
Any idea guys? It is driving me crazy!!!

---

### Post by linux_tech on 2008-12-03
from terminal you can also try the following to shutdown:

sudo poweroff,  sudo shutdown, sudo reboot,  sudo halt 
ie
```
sudo shutdown -h now
```
ref-
[http://www.poplog.org/docs/popdocs/pop11/unix/shutdown](http://www.poplog.org/docs/popdocs/pop11/unix/shutdown)


or

CTRL+ ALT+ F5
to go to text mode, then login and then type:
/sbin/shutdown -h now

Are you able to shutdown using any of these?

---

### Post by linux_tech on 2008-12-03
Also try these suggestions

go to bios setup utility and load the setup default values

try changing the power management settings

System-->Preferences-->Sessions-->Power Manager
Is it enabled or disabled?
What is selection for Action (General tab), "when power button is pressed"? Try "ask me" or "shutdown"

---

### Post by mrjerryk on 2008-12-03
also make sure the bios isn't set to turn the computer on when a key is pressed or the mouse button is pressed.  That's the way I have mine setup.

---

### Post by dirac14 on 2008-12-04
> **linux_tech said:**
> from terminal you can also try the following to shutdown:
sudo poweroff,  sudo shutdown, sudo reboot,  sudo halt 
ie
```
sudo shutdown -h now
```

Are you able to shutdown using any of these?


In fact i tried sudo shutdown and it still restarts. What i have noticed though, is that it restarts only when it is on ac power and not when it runs on battery. I cannot understand..

---

### Post by shane2peru on 2008-12-20
I have the same problem with a Toshiba satellite as well.  A new Satellite to be more precise.  This is a glitch.  If I suspend it automatically starts back up immediatly after that I can shut it down correctly.  Also my battery is not recognized until I suspend first then it is recognized.  However if I suspend, then my network doesn't work correctly. :)  Gotta love it.  I just shut down and then hit power button when it is all done.  Annoying though none the less.

Shane

---

### Post by squiddie on 2008-12-26
Same here on a Toshiba Satellite P300D running 8.10.

- shutdown reboots
- battery not recognized

Perhaps a ACPI problem(?)

iirc it worked with 8.04.1. I'm not too shure about that as I replaced it with 8.10 after a few boots so perhaps 8.04 always ran from battery.

---

