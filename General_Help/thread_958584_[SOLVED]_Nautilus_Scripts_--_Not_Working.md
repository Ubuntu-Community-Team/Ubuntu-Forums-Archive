---
title: "[SOLVED] Nautilus Scripts -- Not Working"
date: 2008-10-25
forum: General Help
---

### Post by praxis1949 on 2008-10-25
Greetings,

This is probably another post to illustrate my basic ignorance. I have scripts for starting and stopping Tomcat in the {user}/.gnome2/nautilus_scripts, and they show up fine on the Desktop (right click) scripts menu. They work fine in the terminal window from a Desktop file copy, or from the nautilus_scripts directory IF I use "./" before the command. There must be some path command screwup, but damned if I know where it is. 

Is there some place where Nautilus is configured? I am using CLASSPATH commands for java and Tomcat, which I EXPORT on startup. Could this be the source of the  problem (i.e. my path commands are screwed up on startup)?

Put me out of my misery!

John S
Gatineau, QC, Canada

---

### Post by praxis1949 on 2008-10-26
Perhaps the problem would have been more obvious if I had printed the script. It was as follows:

#!/bin/bash
sudo /usr/share/tomcat6/bin/./startup.sh

Solution:

#!/bin/bash
gksudo /usr/share/tomcat6/bin/./startup.sh

Gotta use gksudo (no idea why)

---

