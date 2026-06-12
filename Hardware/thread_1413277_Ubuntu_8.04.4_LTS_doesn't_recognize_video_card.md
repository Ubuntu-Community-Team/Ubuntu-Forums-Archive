---
title: "Ubuntu 8.04.4 LTS doesn't recognize video card"
date: 2010-02-22
forum: Hardware
---

### Post by Objekt on 2010-02-22
Yesterday I installed Ubuntu 8.04.4 LTS 32-bit.  While I have an Nvidia GeForce 9800 GTX+ video card, Ubuntu doesn't seem to recognize it.  The "Hardware Drivers" applet does not offer to install anything.

I forced the issue by downloading and installing the Nvidia 190.53 Linux drivers package manually.  I had to shut down Xserver, run the Nvidia .run file, reboot, etc.  But it didn't work.  Upon startup, I got a very messed up display.  I then had to designate my monitor info manually.  After getting to the desktop, I ran nvidia-settings.  It told me that the Nvidia driver is not being used.

WTF?  How do I get the Nvidia driver package installed & start using it?

---

### Post by Objekt on 2010-02-23
Also tried the EnvyNG package.  It refused to install anything, saying it couldn't detect any Nvidia hardware.  

What the heck happened with Ubuntu 8.04.4?  

Update:

Ubuntu 8.04.3 has exactly the same problem.  I recently installed it on a different machine, also with Nvidia video hardware, without issue.  WTF?!

---

### Post by Objekt on 2010-03-12
Anyone else?  Bueller?  This is a pretty huge bug.  Maybe later today, I'll post a bug report.

---

### Post by subedistra7 on 2010-03-12
> **Objekt said:**
> Anyone else?  Bueller?  This is a pretty huge bug.  Maybe later today, I'll post a bug report.

hardy has a bug with nvidia that wont work with drivers later than something like 173 unless you modify some stuff.

---

### Post by Objekt on 2010-03-12
> **subedistra7 said:**
> hardy has a bug with nvidia that wont work with drivers later than something like 173 unless you modify some stuff.

Ahh...that may explain it!  When I installed 8.04.3 LTS on a different machine a few months ago, the current Nvidia driver may have been 173 or earlier.  I'll have to track down version 173 or older & see if it works for 8.04.4 LTS on my machine.

Thanks!  I was beginning to wonder if I would ever get a hint.

---

### Post by subedistra7 on 2010-03-12
> **Objekt said:**
> Ahh...that may explain it!  When I installed 8.04.3 LTS on a different machine a few months ago, the current Nvidia driver may have been 173 or earlier.  I'll have to track down version 173 or older & see if it works for 8.04.4 LTS on my machine.

Thanks!  I was beginning to wonder if I would ever get a hint.

np.

---

### Post by Objekt on 2010-03-13
This keeps getting weirder.  I was messing around some with 8.04.4 LTS last night, and just for kicks I tried installing the 190.53 drivers again.  I got some error messages, but it appears to have worked anyway.  When I boot 8.04.4 now, I get a normal display, and I can save the configuration to the xorg.conf file using the nvidia-settings applet (running it with gksudo of course).

I can only guess that some update has fixed whatever the original problem was.  I'm sure that if I did a fresh 8.04.4 LTS install, I would have the original problem all over again.

I'm marking this "solved," since I now know there can be a problem with the LTS's and newer Nvidia drivers.

---

