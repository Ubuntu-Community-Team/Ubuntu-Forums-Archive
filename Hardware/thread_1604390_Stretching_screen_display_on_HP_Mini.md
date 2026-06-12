---
title: "Stretching screen display on HP Mini"
date: 2010-10-24
forum: Hardware
---

### Post by Riothamus on 2010-10-24
Hello everyone.

I'm a new Linux user, trying to learn my way through the OS. I've installed Ubuntu on my HP Mini, but unfortunately, that netbook has a screen which is frequently too small to display some windows or run other programs. On Windows, this is solved by going to Advanced Settings --> Monitors and unchecking a box that says "Hide Display Settings That This Monitor Cannot Display." After that, it allows you to choose more display options, which are too big for the screen, so that way when you move your mouse to the edge of the screen, it scrolls over so you can see the rest of the screen.

Unfortunately, Ubuntu's Monitor program in System Preferences doesn't seem to provide this feature. By doing an Internet search, I've found that you need to manually reconfigure the xorg.conf file in order to do this. I followed the instructions on this page: [http://odkq.com/virtualres.html](http://odkq.com/virtualres.html) to do so. After following the initial instructions, I found that nothing changed, probably because the HP Mini has an Intel graphics driver, so I had to make the changes under the Troubleshooting: Intel Cards section as well. However, when I do that, on starting GDM again, I got the message: "VESA: Kernel modesetting driver in use, refusing to load," and a message that Ubuntu was running in low graphics mode.

So I was wondering if anyone else has found a way to start a virtual resolution which will stretch the screen so I can run those programs whose windows are too large for the physical screen.

---

