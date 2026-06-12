---
title: "Nvidia 9600GT Reverts to low graphics mode"
date: 2008-11-26
forum: Hardware
---

### Post by drwhut on 2008-11-26
Hi, I am currently running an Nvidia 9600GT and have been for quite some time. I switched to Linux full time about 2 months ago and haven't looked back.
I have just upgraded my OS from Hardy to Intrepid. Now previously I force installed the 177 drivers with Envy and it all worked really quite nicely. I had full compiz support, ran dual monitors on seperate X servers and even had some simple 3D games running. But in an attempt to diagnose why I couldn't get a source game working in Wine, I decided to upgrade to a version where the card's drivers are supported in the repositories. But ever since upgrading I am being forced into low graphics mode whenever I try it install drivers either the 177 or the 173.
I looked through the Xorg log and the only error it's returning is 

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Also, Envy won't let me install either returning the error
"EnvyNG has detected that the headers for your kernel are missing and cannot be installed"

I am personally completely stumped. I don't know squat about messing with the Xorg so any suggestions would be exceptionally appreciated.

---

