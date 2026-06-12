---
title: "No OpenGL support on this system errors"
date: 2009-04-12
forum: Hardware
---

### Post by dopefish7590 on 2009-04-12
Hey guys,

Recently I've been having problems with my SDL. When I try to run something like Mupen64Plus (N64 emulator for Linux) and run anything that requires SDL, it says there is no video device available. When running in the terminal it says in the terminal window "No OpenGL support on this system". Which is weird because "glxgears" runs just fine and any GL-specific program will run just fine as well.

The problem started when I compiled the latest version of SDL so I could get some stuff to work, but I could only get certain SDL programs working (VisualBoyAdvance and stuff worked but not much more) Nothing acknowlaged that I had a video card and a working GL instalation. After browsing a few forums they said to install the xorg-dev before recompiling SDL, so I did this and now it detects the video card, but not working GLX.

The last time a problem like this occured was when I installed official drivers and it screwed up xorg.conf. But this time my xorg.conf has remained identical since the last time everything worked.

Any help would be greatly appreciated, thanks in advance.

---

