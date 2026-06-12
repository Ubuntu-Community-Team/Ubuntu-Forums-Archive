---
title: "Ubuntu Studio 8.10 with nvidia display problems"
date: 2008-11-24
forum: Hardware
---

### Post by PySikE on 2008-11-24
Hi! time ago I installed one of the earlier versions of Ubuntu Studio to use as a "proffesional" digital workstation, it failed for a lot of reasons.
One of them is the display configuration even in the new one 8.10, I tryed everything, first off install/activate the Nvidia drivers from the hardware drivers(I have a BFG Nvidia 7600 GS OC) when rebooting the pc the X-conf says "Failed to load....." back to restore the xorg agian, so I tryed the same by hand using the console or using the envy method, nothing.
After a while checking for a solution and reading usless info in forums I realised that I'm missing something.
Hope someone can give me a useful solution.

---

### Post by PySikE on 2008-11-25
Any comments?...

---

### Post by dabl on 2008-11-25
Are you saying it runs OK with the "nv" driver?

EnvyNG should work, but maybe it will help to give you a detailed procedure.  I recommend doing it like this:

First get out of the X server with Ctrl-Alt-F1, then log in at the CLI and shut down the X server with

```
sudo /etc/init.d/gdm stop
```

then do these:

1. Back up your existing xorg.conf file
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```


2. Install and run EnvyNG

```
sudo apt-get update && sudo apt-get install envyng-core
```

```
sudo envyng -t
```


Choose #1 "Install Nvidia driver", and follow guidance to choose a driver.

3. When you are returned to the CLI prompt, run the Nvidia xorg configuration utility:

```

sudo nvidia-xconfig
```


4. When it is done writing a new xorg.conf file, restart the X server with

```
startx
```

Then, if you don't like the resolution, do Alt-F2 "gksudo nvidia-settings" and set the resolution as you want it for default.  It's best to leave the refresh rate set on "Auto".  When you have it the way you want it, click the "Save to X Configuration File" button, and save it.  Now it's your default setting.

---

