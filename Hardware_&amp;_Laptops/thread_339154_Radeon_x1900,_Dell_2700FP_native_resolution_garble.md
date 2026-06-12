---
title: "Radeon x1900, Dell 2700FP native resolution garbled"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by ctrlaltdeath on 2007-01-15
I've been trying my best to search for a solution to this on my own, but I can't find anything close to what's going on.  After using Ubuntu on my work computer (setting it up and using it has been a complete breeze) I decided to switch to Ubuntu as my primary OS on my home machine as well.

The problem is, I'm getting weird output on my screen (a Dell 2700FP flat panel) when I'm running in the monitor's native resolution of 1600 x 1200.  My card is a Radeon x1900, and I've gone through the whole driver install process in the "ATI Binary Driver Howto".  fglrxinfo displays the correct information, and glxgears runs smoothly and gives pretty nice FPS. 

The issue is that on the bottom part of the screen, I'll see sections from open windows and such.  For instance, right now about half of the toolbar for Firefox is displaying on the bottom of the screen.  If I open Synaptic, the package description section of the window displays in the bottom left of the screen as well as in the proper window.  I don't really know if I can describe it better than that...it's just displaying bits of open windows at the bottom of the screen.   Also, if i use the scroll wheel or drag the slider to scroll down a page in a browser, the output in the browser window becomes all garbled....if I use PgUp/PgDn, everything displays properly.  I've tried searching for anybody else with similar issues, but it's kind of hard to describe this problem in search terms.

If I change to a different resolution, everything works fine and the problem goes away.  As soon as I switch back to the native resolution, the same thing happens again.  Other than this, everything else seems to be working great...the drivers are installed, 3D acceleration is working, etc.  but this is extremely aggravating. 

I've attached the contents of my xorg.conf file.  Any help would be greatly appreciated...up to this point I've been able to resolve all my problems through searching the forums.  You guys all do a great job as a supportive community, and I really appreciate that.  Hopefully I'll be able to start dispensing answers as I learn some more stuff ;)

---

### Post by d00dz on 2007-05-29
I'm experiencing the same problem.

Hoping anyone can provide input.

---

