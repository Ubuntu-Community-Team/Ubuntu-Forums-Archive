---
title: "libchipcard-tools"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by thunderkyss on 2009-02-14
What does this mean:

> E: libchipcard-tools: subprocess post-installation script returned error

exit status 1

and how do I go about troubleshooting what the problem is??

Is there a crash log, change log, or something that would provide more details.


FYI, I was trying to install the Gstreamer codecs.

---

### Post by Partyboi2 on 2009-02-15
Normally you can get more details by viewing the lines above the error, you would need to use the terminal.
So open a terminal and try installing it using apt-get
```
sudo apt-get install libchipcard-tools
``` Then see why it was not installing.

You can also look at /var/log/apt/term.log to see more info.

---

