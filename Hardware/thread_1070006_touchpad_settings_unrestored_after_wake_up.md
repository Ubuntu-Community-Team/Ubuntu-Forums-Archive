---
title: "touchpad settings unrestored after wake up"
date: 2009-02-14
forum: Hardware
---

### Post by wolterh on 2009-02-14
After waking up my computer from a suspend, either a suspend to ram, or a suspend to disk, my touchpad settings are not restored.

All the touchpad works fine, but the acceleration variables get defaulted.

I tried adding a script that would fix the variables to /etc/acpi/resume.d but it didn't work; I don't think it even got executed.

So, how can I fix this? Am I the only person having this issue?

My computer:
Dell XPS m1530
2.20 GHz Core 2 Duo Processor
4GB RAM
nVidia GeForce 8600M GT

---

### Post by BurakkuChi on 2009-02-14
I'm having the same issue with Intrepid Ibex. This is just a shot in the dark, but I think it may be because ~/.gconfd/saved_state does not contain any information on the touchpad... Can anyone confirm that this may be the issue?

---

### Post by BurakkuChi on 2009-02-15
woli, have you checked System->Preferences->Sessions? There should be an entry called "Touchpad" with the command "gsynaptics-init --sm-disable"

---

### Post by wolterh on 2009-02-15
There is such entry in my gnome-session-properties, but the problem is that niether hibernate, nor suspend, run start up scripts. Now, when I turn on my computer, I normally get the touchpad working with my preferences as I left them. This problem only occurs after hibernate or suspend.

---

### Post by BurakkuChi on 2009-02-16
Looks like this issue is being tracked via [https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/303595]("https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/303595").

---

### Post by wolterh on 2009-02-16
Well, that could work, but my problem is even bigger, solely the command ```
gsynaptics-init
``` disables my touchpad's motion.

Now, to enable my touchpad each time I engineered this little script
```

#!/bin/bash

# Restore my touchpad settings
synclient AccelFactor=0.131 MinSpeed=0.333 MaxSpeed=1

```

---

