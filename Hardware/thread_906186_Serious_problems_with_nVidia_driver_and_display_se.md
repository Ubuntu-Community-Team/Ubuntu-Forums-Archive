---
title: "Serious problems with nVidia driver and display settings"
date: 2008-08-31
forum: Hardware
---

### Post by wendigo10 on 2008-08-31
I had the latest nVidia driver installed, everything worked fine. Then, I tried to run a game, it had a low FPS, so I disabled effects. Later, I tried to change back to "extra", but it won't let me. I read some topics here, I installed that glx, re-installed the drivers. "compiz --replace" didn't work.

Now I can't turn on the effects. The Nvidia driver IS installed, but it persits, I tried to uninstall it and re-install.
Here's the output when I run compiz -

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

The display resolution application doesn't work, and the nvidia X server settings say that the nvidia driver isn't in use.

Please, help me, I'm desperate.
Thank you.

---

### Post by overdrank on 2008-08-31
> **wendigo10 said:**
> I had the latest nVidia driver installed, everything worked fine. Then, I tried to run a game, it had a low FPS, so I disabled effects. Later, I tried to change back to "extra", but it won't let me. I read some topics here, I installed that glx, re-installed the drivers. "compiz --replace" didn't work.

Now I can't turn on the effects. The Nvidia driver IS installed, but it persits, I tried to uninstall it and re-install.
Here's the output when I run compiz -

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

The display resolution application doesn't work, and the nvidia X server settings say that the nvidia driver isn't in use.

Please, help me, I'm desperate.
Thank you.

Hi and welcome, How did you install the drivers? If the nvidia settings are saying you are not using the driver then you are not. If you installed manually then did a update you may have to install them again.

---

### Post by wendigo10 on 2008-09-03
I tried both manual installation and installation using the hardware drivers wizard.
I guess it's a bug, I re-installed Ubuntu.

Thanks.

---

### Post by bunny rabbit on 2008-09-04
Hey, Maybe it is a good idea to let this program called 'envy' install it for you. Envy is in the repositories, simply search for envy in synaptic. Maybe you need to check boxes in: *system*->*software* *sources*(you know: muliverse, univers etc..)first.
Envy will probably be under *applications*->*system tools*.

All the best,

---

