---
title: "Upgrade manager doesn't notify of the new release"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2009-04-30
When I do the suggested command to "force" upgrade-manager to see the new release  of Jaunty (update-notifier-kde -u)on an Intrepid machine.

It just returns:
```
Traceback (most recent call last):          
  File "/usr/bin/update-notifier-kde", line 28, in <module>
    from PyKDE4.kdecore import *                           
RuntimeError: the sip module supports API v3.0 to v3.7 but the PyKDE4.kdecore module requires API v3.8
```

This is on a different machine to my main one, if you're wondering why I'm trying to upgrade when my profile says I'm already on Jaunty. :)

---

### Post by Ubuntiac on 2009-04-30
So I've now tried purging and re-installing python-kde, update-notifier-kde and even kubuntu-desktop to no effect...

Any ideas anyone?

---

### Post by Sef on 2009-04-30
In Ubuntu, you would check this way: System > Administration > Software Sources > Update > Release Upgrade?  Is it set to Normal Releases or Long Term Support Releases Only or Never?   Set it to Normal Releases, if it is not.

KDE would have something similar.

---

### Post by Ubuntiac on 2009-04-30
Thanks for the suggestion Sef,

I got it working just now by using Synaptic instead of Adept Manager to upgrade. Seems to have done the trick, although I have no idea why adept-notifier was giving me that error. Anyway, all is good, thanks for your help!

---

