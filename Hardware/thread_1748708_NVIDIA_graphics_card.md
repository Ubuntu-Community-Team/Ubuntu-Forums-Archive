---
title: "NVIDIA graphics card"
date: 2011-05-03
forum: Hardware
---

### Post by cliftonbazaar on 2011-05-03
Everytime my computer re-starts it asks the same question -
> Ubuntu is running in low graphics mode.
(EE) NVIDIA:Failed to load the nvidia kernal module
(EE) Failed to load module "nvidia" (Module-specific error, 0)
(EE) No drivers availableI hit the okay button and then I choose to run Ubuntu in low graphics mode - and everything works fine (including high graphics!).

The problem is that the server is too restart itself in case of a blackout, but because of this question being asked the server is not active (and my website is offline) until someone clicks the okay button.

Other information -
A) I have the latest NVIDIA drivers installed, when the computer is running the drivers work fine as I have fantastic graphics (even though it is a simple server).
B) If I remove the Nvidia drivers I can only get the screen to be 360*240, make it very hard to do anything.
C) Have tried un-installing the NVidia drivers and re-installing them (done this many times) but nothing changes.

So it seems that the computer loads in the Nvidia drivers even though it tells me that it can't find the drivers.

Is there a way I can avoid the computer asking me about the Nvidia drivers when it is booting up and simply start in low graphics mode?

---

### Post by mörgæs on 2011-05-04
This thread explains more about the problem:

[http://ubuntuforums.org/showthread.php?t=1743386](http://ubuntuforums.org/showthread.php?t=1743386)

---

