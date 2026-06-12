---
title: "Screwy file permissions after upgrading HD, dbus and sudo errors"
date: 2008-10-04
forum: General Help
---

### Post by tehschulman on 2008-10-04
After upgrading my EEEPC 1000h's internal hard drive I've been having a rocky time with Ubuntu. When I boot into my system I can get to my X desktop fine, but many of my boot services and system services are unaccessible. I've traced this problem back to dbus, dbus does not have the proper permissions to allow my user to interact with my hardware (wifi specifically) and also does not allow me to use any system tools (Network Manager for example)

I know that this has to do with a permissions error, I just don't know how to quite fix it. When I copied my ubuntu install to my new hard drive I mounted the new drive as an external device, copied everything, then transfered it into my laptop. To my knowledge permissions were preserved, but it does not look like that is the case.

Is there a way I can restore all of the folder and file permissions on my system? Which directories and config files should I absolutely change the permissions and owner on for root? Please post some commands I can give the output to so I can diagnose the issue. Thanks!

---

### Post by tehschulman on 2008-10-04
bump

---

### Post by tehschulman on 2008-10-05
The error I get specifically when I try to use any of the system tools is:

```

The configuration could not be loaded
You are not allowed to access the system configuration.

```

---

### Post by tehschulman on 2008-10-05
Is this the right forum for this question? I'd appreciate it if a mod could move this to the appropriate place. Thanks

---

