---
title: "Kernel Modesetting (KMS) / compiz problem..."
date: 2011-08-30
forum: Hardware
---

### Post by Marco.75 on 2011-08-30
Hi, 
I have an Acer 5100 laptop with an ATI Radeon Xpress 1100 graphic chip.
There is a well documented issue with the above machine suspend feature (when resuming the screen is garbled) and somewere I've found the only solution: disabling KMS.... so I added to my boot options, besides "quiet splash" also "nomodeset" and this solved the suspend/resume issue.
There's another problem, by the way: with KMS disabled, I have no more shadows on windows, no more transparency in the terminal emulator, it seems that overall compiz isn't working.
To make sure KMS is the culprit I turned it back on, and all the graphic effects came back too...
so... do I have to choose between a nice looking desktop and a working suspend/resume feature? Is there a solution?

---

