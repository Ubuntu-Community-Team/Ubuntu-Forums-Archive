---
title: "Solution for displaying on projector in Gutsy (Workaround)"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by mawxcarroll on 2007-11-30
In Feisty, I could hook my laptop up to a projector and ctrl-alt-backspace and my display would be on the projector screen and not the laptop, which was fine for presentations.  The same does not work for me in Gutsy.  It seems others were having a similar problem, so here's my (inelegant) workaround solution:

1. cd /etc/X11
    sudo cp xorg.conf xorg.conf.WorkingSingleScreen

2. Connect the projector and then do System->Administration->Screens and Graphics.  Choose screen 2 to be a secondary screen, extended.  What you really want is mirror default screen, but it won't seem to let me select that here...

3. ctrl-alt-backspace.  You should have a very ugly dual view display.  But now if you go to System->Administration->Screens and Graphics, you should be able to select screen 2 to be "mirror default screen."  Select that and "ok".

4. ctrl-alt-backspace.  You should now have display only on the projector screen.  Works for presentations.

5. cd /etc/X11
   sudo cp xorg.conf xorg.conf.ProjectorScreen

 You now have two xorg.conf files, one corresponding to projection and one corresponding to normal operation.

It's a bit inelegant (just a bit), but to switch between them just go into /etc/X11 and copy the one you want onto xorg.conf and then ctrl-alt-backspace.

It's a relatively easy way to get projector output.  I could only choose 800x600 at best, but that works fine.

(Note: If something gets really broken and you can't get your graphical interface to start, you can just go to /etc/X11 and copy the working version of xorg.conf.whatever onto xorg.conf and do ctrl-alt-backspace.)

-tom

---

### Post by daengbo on 2007-11-30
You should be able to use xrandr to just add the second screen (projector) when you need it and disable when you're done. You can then write two (short) scripts and place them on your desktop. Take a look at xrandr.

---

