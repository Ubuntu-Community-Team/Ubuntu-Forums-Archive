---
title: "suspend/resume script failing"
date: 2012-05-13
forum: Hardware
---

### Post by n00b512 on 2012-05-13
I have a startup script that changes my MAC address for me, but I  noticed that after a successful suspend/resume it was changed back.  So I  did some research and put together a resume script that changes it  back.  I put in in /etc/pm/sleep.d/99_changemac-suspend.  It actually  points back to the original script in /etc/init.d that does the MAC  change on boot and outputs $1 to a file so I can see that it ran and  with what input.

The script runs fine when I execute it manually and I can tell it runs  on resume because the output file shows the expected input of "resume",  but my MAC is not as it should be.  I can only assume that even with a  start order of 99 something else is running after it which reinitializes  the NIC and loses my custom settings.  

What can I do to troubleshoot this issue?  Is there a way to force my script to run last?
I'm using 11.11

---

### Post by Toz on 2012-05-19
The scripts in /etc/pm/sleep.d run alphabetically ascending (0, 1, 2, a, b, c) during suspend and descending (c, b, a, 3, 2, 1) during resume. Try renaming your script to 02_changemac-suspend so it runs later in the process. See if that helps.

---

