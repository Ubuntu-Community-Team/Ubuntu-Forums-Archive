---
title: "Dell docking station monitor not working"
date: 2009-03-21
forum: Hardware
---

### Post by georgemcbaingage on 2009-03-21
Dell latitude D620 with NIVDIA 173.14.12 driver all works well delighted but no external signal when in dell docking station so external monitors all dies after Ubuntu displayed can't get the settings right anybody help?;)
I tried with windoze machine all working fine

---

### Post by yarlagdd on 2009-05-02
Any subject matter experts care to comments on this? I am also facing the same issue.

---

### Post by robjeppo on 2009-06-13
I also have this problem. Specifically when in a dock with monitor stand and thus the laptop lid closed.

Boot graphics and text console are visible and text console is visible again after [Ctrl]+[Alt]+[F(any)].

---

### Post by mojorising on 2009-06-15
Hi, there. I'm not sure why but this seems to be an issue with the proprietary NVidia driver. Try disabling it in the System > Administration > Hardware Drivers utility. Then reboot the machine and plug it into the dock. The laptop should be in the dock at boot for this to work. 

When using the default driver, he only issue I have is that I can't hot-swap the laptop from the dock while it is running -- that just won't work. I have a Dell d630 at work with a Dell dock and NVidia video. 


Mike

---

### Post by john_navarro on 2009-06-16
I have the Dell D630 with Intel video and a Samsung 2253BW monitor and I'm stuck looking at 1024x768 on this monitor  :(

---

### Post by john_navarro on 2009-06-18
My video issues were fixed by downgrading the video driver using these instructions:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by recluce on 2009-06-18
I had similar problems and posted the solution (workaround) here:

[http://ubuntuforums.org/showthread.php?t=1116937](http://ubuntuforums.org/showthread.php?t=1116937)

Hint: try pressing "Scroll-Lock" and "F8" on your external keyboard when you hear the Login-Screen Jingle...

---

