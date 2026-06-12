---
title: "gnome-pilot hotsync issues"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by Plank117 on 2006-05-27
I have been trying to install a JVM on my old Palm m130 with no success. How do I use gnome-pilot to stick prc's on a Palm? gnome-pilot recognizes that my handheld is there, but even when I have the file conduit enabled, I can't install any of the prc's I put in my handheld's base directory. What gives? Is there a way to fix this or a is there better software available?

---

### Post by wastrel on 2006-06-06
use the command line tools...

pilot-xfer -p <port> -i <file to install>

man pilot-xfer for more info.

You can also check out jpilot.  

Note:  kill gpilotd before trying to sync using jpilot or pilot-xfer

---

### Post by Plank117 on 2006-06-06
Spiffy. But how do I go about killing a process/program/application/etcetera? I never learned the command.

---

### Post by wastrel on 2006-06-07
First remove the gnome pilot applet from your panel.  Right-click and choose "Remove from Panel"

Now kill gpilotd.  System->Administration->System Monitor.  Processes tab.  Find gpilotd, hilight and click the End Process button.

Alternatively, "killall gpilotd" from the terminal might work.

---

