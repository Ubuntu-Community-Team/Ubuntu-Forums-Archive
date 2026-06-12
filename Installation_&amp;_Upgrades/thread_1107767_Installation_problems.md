---
title: "Installation problems"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by sub-d on 2009-03-27
This maybe related to X server problems?

Downloaded latest Ubuntu OS and did a new install.
This is as far as it got ...

"Installing GNOME display manager   OK
 Installing System Tools and Backends system-tool-backends  OK
 Starting deferred execution scheduler atd  OK
 Starting periodic command scheduler crond  OK
 Enabling addition executional binary formats binfmt-support OK
 Checking battery state   OK "

screen blinks a few times, freezes then I get this message ..

"The display server has been shut down about 6 times in the
 last 90 seconds.  It is likely something bad is going on.

 Waiting for 2 minutes before trying again on display: 0"
 OK

Since I'm new to this, I'm not sure what steps to take next.
Reading other threads makes me think its a video driver problem?

My system:

Medion PC
250GB Seagate SATA Hard Drive
Monitor:  Asus 19" LCD, Native resolution: 1440x900 @ 60Hz
Graphics card: NVIDIA GeForce 8500GT with HDMI connection

Any assistance is greatly appreciated !!

Cheers,
sub-d

---

### Post by Pumalite on 2009-03-27
Were you able to boot a Live CD without any problems; reaching the Desktop?

---

### Post by sub-d on 2009-03-27
Yes, had no problems running as a live CD, the screen
appeared to be OK, everything was accessible.

Cheers,
sub-d

---

### Post by Pumalite on 2009-03-27
Copy and save the xorg.conf file of your Live CD and replace your installion one with it. Let's see.

---

