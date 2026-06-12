---
title: "Start up python script minimized"
date: 2008-07-18
forum: General Help
---

### Post by corblimey on 2008-07-18
My google-fu has let me down here, and I'm sure it's something that can be done.  I've got a python script that I want to run everytime I log in.  So I added it to my sessions as a startup.  All well and good, except that it starts up and takes up the full screen.  I want it to run minimized (or even just run and then quit).  Is there anything I can do here?

---

### Post by y-lee on 2008-07-18
hmm my solution to that problem would be to wrap a gui around your python code using something like [wxPython]("http://wxpython.org/"). The window then could be coded to start minimized and terminate when done. 

A simpler solution might be to use the [wmctrl]("http://www.sweb.cz/tripie/utils/wmctrl/") command to minimize the window. Put your pyhthon scriptname statement in a bash script followed by maybe wmctrl -k on.

There may be and probably are other maybe even better solutions but those two are the first i thought of. Hope it helps.

---

