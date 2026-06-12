---
title: "[SOLVED] Open Office in 4.1.1?"
date: 2008-09-22
forum: General Help
---

### Post by bconover on 2008-09-22
Whenever I run OpenOffice under KDE 4.1.1, everything whacks out. The panel at the bottom of my screen flickers, and my desktop turns black. IF I close out of OpenOffice, this goes away after about 10 seconds, and everythign is normal. 

Any ideas to prevent this? It's kind of annoying having everything flickering on and off while I'm trying to work on a document  :mad:

Help is greatly appreciated!

bconover

---

### Post by Pro-reason on 2008-09-22
Yes, I came across that too.  Do you have 3D effects enabled?  I'm not sure whether it's a bug in OpenOffice, KDE or both.  Perhaps it should be reported.

---

### Post by bconover on 2008-09-22
Disabling all effects under System Settings -> Desktop (Enable Desktop Affects, uncheck) stops this problem. Seems OO isn't taking too well to the effects :) I might fiddle some more and see what happens.

---

### Post by bconover on 2008-09-22
Changing the Compositing Type under System Settings -> Desktop ->Advanced Settings from OpenGL to XRender seems to have solved this problem (though the animations throughout the rest of the system seem a little slower on XRender than with OpenGL, but only slightly so). Not sure if I should mark this "Solved" yet, anyone know how to get OO to run properly with Desktop Effects using OpenGL?

EDIT:

Well, XRender seems to work fine for everything else too, I guess this is solved.

---

