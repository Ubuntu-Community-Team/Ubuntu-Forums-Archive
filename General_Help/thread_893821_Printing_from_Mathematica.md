---
title: "Printing from Mathematica"
date: 2008-08-18
forum: General Help
---

### Post by stringkarma on 2008-08-18
I just wanted to complete a discussion that was ongoing prior to the archiving and "read only"-ing of the older threads.

In [this thread]("http://ubuntuforums.org/showthread.php?t=631477&highlight=print+mathematica"), we were discussing graphics and printing problems in mathematical software. To answer someone's question involving his printers not appearing in the print dialog, I have seen that the [launchpad]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/197163/comments/81") on this topic has provided an answer.

Basically it comes down to Mathematica looking for its printers in the wrong (old) place. To correct it (as per the launchpad link above) do these steps:

edit the cups (printer system) configuration file: ```
sudo gedit /etc/cups/cupsd.conf
``` at the bottom of this file add the line: ```
Printcap /etc/printcap
``` save the file and close gedit.

Now simply restart cups with the command: ```
sudo /etc/init.d/cupsys restart
``` and it should show your configured printers.

---

