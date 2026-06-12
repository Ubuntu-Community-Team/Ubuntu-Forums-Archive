---
title: "Switching between screens question, can anyone advise?"
date: 2009-02-11
forum: Hardware
---

### Post by jobsonandrew on 2009-02-11
Hi,
I have an Inspiron 1720 with 8600 GT that has a key (Fn+F8 ) to switch between video modes like this:
Panel -> Panel+External -> External
Surprisingly, this works fine in Ubuntu 8.10 with Nvidia driver 177 (installed via the 'restricted drivers' tool). The screens I'm talking about are:
Laptop Panel - 1440x900
32" TV (via VGA) - 1366x768
The only problem is, it doesnt seem to be able to automatically set the resolution of the external screen (the TV). i never use the 'both' mode and i dont think it can output 2 different resolutions at the same time.

Is there a way I can setup my xorg.conf to say "when screen 1 is active, the res is 1440x900, when screen 2 is active, the res is 1366x768, when they are both active, the res is 1366x768"?

Also, can Ubuntu remember what screen it was using last when it boots? and what about if I just disconnect the VGA cable?

---

### Post by nixscripter on 2009-02-14
The problem might be that the TV's resolution isn't detecting properly. Try running this in a terminal with the TV plugged in (but not active): ```
xrandr -q
``` and see what resolutions are available.

---

