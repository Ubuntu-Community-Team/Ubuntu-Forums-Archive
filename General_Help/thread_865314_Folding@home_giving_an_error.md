---
title: "Folding@home giving an error"
date: 2008-07-20
forum: General Help
---

### Post by Rhapsody on 2008-07-20
I recently checked on Folding@home (version 6 beta SMP client) and saw the following:

```
[18:23:36] - Reading up to 3721632 from "work/wudata_02.arc": Read 3721632
[18:23:36] - Reading up to 1775336 from "work/wudata_02.xtc": Read 1775336
[18:23:36] goefile size: 0
[18:23:36] logfile size: 16911
[18:23:36] Leaving Run
[18:23:41] - Writing 5518279 bytes of core data to disk...
[18:23:41]   ... Done.
[18:23:41] - Shutting down core
[18:23:41]
[18:23:41] Folding@home Core Shutdown: FINISHED_UNIT
```
This was unusual, so I stopped and restarted it. I got this:

```
[18:37:41] Working on Unit 02 [July 20 18:37:41]
[18:37:41] + Working ...
[18:37:41]
[18:37:41] *------------------------------*
[18:37:41] Folding@Home Gromacs SMP Core
[18:37:41] Version 1.74 (November 27, 2006)
[18:37:41]
[18:37:41] Preparing to commence simulation
[18:37:41] - Ensuring status. Please wait.
[18:37:41]
Client is running.
```
Followed by this:

```
[18:37:41] Preparing to commence simulation
[18:37:41] - Ensuring status. Please wait.
[18:37:41] - Shutting down core
[18:37:58] put
[18:37:58] - Starting from initial work packet
[18:37:58]
[18:37:58] Project: 0 (Run 0, Clone 0, Gen 0)
[18:37:58]
[18:37:58] Error: Could not write local file.  Exiting.
[18:37:58] - Shutting down core
```
I then decided to stop the client for now. What's going on?

---

### Post by Julian David Pitt on 2008-07-20
I believe you would get more joy if you posted this on the Folding forum at [[COLOR="Blue"]http://foldingforum.org/[/COLOR]]("http://foldingforum.org/")

---

