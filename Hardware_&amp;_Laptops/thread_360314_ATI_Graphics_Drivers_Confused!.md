---
title: "ATI Graphics Drivers Confused!"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by inkysplat on 2007-02-13
I've been using linux for years now, but in the past i've never had a 3D supported graphics card so I never needed to install any 3rd party graphics drivers.

However I've recently bought a Dell C521 which has an ATI X1300 128MB.  My Ultimate aim is to get Beryl or Compiz working on the machine.  

I'm using the 64bit version of Edgy at the moment, after a default install it is using the Vesa driver which makes dragging or scrolling windows PAINFULLY slow and annoying.  However I noticed that it will attempt to render GL based Screensavers.  I've followed the guides to get fglrx from the repos, and after installing them, windows can be dragged and scrolled as normal, however it doesn't bother running any GL stuff, glxgears or screensavers.  On running fglrxinfo it says 
> display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Generic
OpenGL version string: 2.0.6234 (8.32.5)

I'm not sure if its meant to say "Generic" (if someone can clear that up)?

Thinking maybe the drivers in the repositories were out of date I decided to use the ones from the ATI site compiling them into .debs like the unoffical guide says and making modules.  However this method leads to Xserver crashing the moment it loads up. I've checked the xorg.conf and it is eactly the same as installing it from repositories.  So I assume its a driver issue.  

Curiously I also installed the Mesa stuff that the howto suggests when removing fglrx, and I get glxgears again and my windows draw fine, but it seems to perform a little sluggish compared to fglrx.

All I'm basically trying to achieve here is to get fglrxinfo to say Direct Rendering "on", so I can move on to getting XGL and Beryl installed.

---

