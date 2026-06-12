---
title: "gpilot falls over ONLY on eToDo"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by bedohave on 2007-04-17
Hello,

Here's the situation:
[LIST=1]
[*]Dell Inspiron 6000, running Feisty beta (upgraded from Edgy)
[*]Using Evolution and Palm T3
[*]gpilot worked flawlessly prior to upgrade (believe it!)
[*]After upgrade to Feisty beta, gpilot still connects and syncs.  It hangs, however, when it starts sync-ing todos with the eToDo conduit.
[*]Using the system monitor, I can see gpilotd end while gnome-pilot applet continues to run.
[*]When I back up then delete all todos on the Palm and in Evolution, the gpilot goes to completion.  eToDo starts and completes (with nothing to sync, of course).
[/LIST]

Where should I start looking for clues?  Where would I find gpilotd logging?  Any other suggestions?


ME

---

### Post by janbockaert on 2007-05-03
i'm affraid i have to confirm this, e-todo hangs when i'm syncing. :(

Palm treo 600 here.

---

### Post by KlfJoat on 2007-05-18
I hate to say it, but "me too!".  
Launchpad bug for this issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot-conduits/+bug/81170](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot-conduits/+bug/81170)

---

### Post by bedohave on 2007-05-21
Hi KflJoat,

Thanks for the pointer to LaunchPad; I'm still learning about that as a resource.

Mike

---

