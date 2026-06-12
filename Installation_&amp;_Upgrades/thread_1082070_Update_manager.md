---
title: "Update manager"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by beetwaste on 2009-02-27
Hi

I've got an elderly laptop PIII/500, running Xubuntu 8.10. Update manager keeps telling me I have updates. When I try to install them, I am finding that it starts downloading the updates, gets  to  about 45%, and doesn't finish downloading. When I upgraded to 8.10, it took about 30 hours on a 1meg broadband connection to do this. Does anyone have any ideas why this is, and what I can do about it?

---

### Post by giarca on 2009-02-27
Open the details menu to see where the update stop. It can be a download from a location you can't reach or doesnt' exist (if you have lot of unoffical repo for example).
Try to disable all unofficial repo and download only from archive.ubuntu.com and security.ubuntu.com.

---

### Post by hansdown on 2009-02-27
Hi beetwaste.

The updates for a fresh install tend to be rather large.

To find a faster mirror, click ```
system> administration> software sources[/CODE

Enter your password.

Click[CODE] ubuntu software
```.

Go to```
 download from
```.

Click it to get the drop down list.

Choose ```
other
```.

Click on```
 best server
```.

It will choose the fastest server to update from.

---

