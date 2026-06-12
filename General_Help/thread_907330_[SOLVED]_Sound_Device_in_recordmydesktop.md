---
title: "[SOLVED] Sound Device in recordmydesktop"
date: 2008-09-01
forum: General Help
---

### Post by RequinB4 on 2008-09-01
How can i tell what my sound device is?  recordmydesktop doesn't seem to autodetect:

> 
Initial recording window is set to:
X:0   Y:0    Width:1440    Height:900
Adjusted recording window is set to:
X:0   Y:2    Width:1440    Height:896
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.


The man page says to use -device <device> to specify the device.  I've tried /dev/snd/seq and the output of "sudo asoundconf list"

Solved:  I had two sound cards - to anyone who gets this bug, try using the option -device hw:1,0

---

