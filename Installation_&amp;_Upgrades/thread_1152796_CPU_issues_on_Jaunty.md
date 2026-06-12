---
title: "CPU issues on Jaunty"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by geoffatmk on 2009-05-08
I have looked through the posts but cannot find a solution to my problem.

I am running Jaunty (upgraded from Intrepid through package manager) on a Samsung Intel PC.

Since upgrading, my CPU as shown by the system monitor is virtually always 100% or thereabouts.

I have run top to see what is happening but top reports a lower CPU usage (circa 70%).  Adding the CPU usage figures in top however, only shows about 25%.  So what is going on?

Are the monitor and top reading the same things?

Does top show ALL running processes or can some be hidden?  (System monitor does not appear to show all processes as far as I can see).

Is there any other way of isolating the processes to see what it is that is causing the problem?

Sometimes if I log out, a dialog box comes up to tell me there is still and unknown process running.  If I cancel the logout at that stage, the processor seems to revert to normal.  It is almost as if the logging out has stopped something in the background and then asked me about another process.  By cancelling the logout, the problem process was stopped and the CPU return to "normal" levels.

Is anyone else facing the same problem?

Can anyone offer any answers please?

Geoff

---

### Post by geoffatmk on 2009-05-08
I seem to have found the culprit.  Like others in other posts I killed off vino-server and instantly the load went down.  to ensure it does not start at boot I have disabled remote desktop (server) in the Preferences:Startup Applications dialog.

It is one thing to find the problem and another to find a solution to why it is happening as from time to time I like to use remote logins.  Can anyone throw any light on why it is happening and if a fix is being looked at?

Geoff

---

