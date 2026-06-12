---
title: "Can't dial up"
date: 2005-01-04
forum: Installation &amp; Upgrades
---

### Post by J.K. on 2005-01-04
I have tried to set up my dial up modem as per instructed in a previos tread, but still can't seem to get any response.
I have been to comp-. sys config-.networking-. add, and put in all the info, but the sytem is unresponsive. when I click on activate, a tick apears next to the dial up account for about a second then disapears.
In the device manager, the modem is listed there.
Where do i go from here.?

---

### Post by ubuntu1 on 2005-01-04
I had the same problem on my Fathers machine. Ignore the usual method and use pppconfig.  Delete your current settings and then sudo and run pppconfig.

You can then add the 'Modem Lights' applet to the top menu panel on the
desktop. By clicking on this applet you can connect/disconnect.

This worked for me, good luck.

---

