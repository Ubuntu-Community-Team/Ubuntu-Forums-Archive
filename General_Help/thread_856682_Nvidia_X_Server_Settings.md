---
title: "Nvidia X Server Settings"
date: 2008-07-11
forum: General Help
---

### Post by gdonwallace on 2008-07-11
It took a bit, but I finally got my monitors setup the way I want.  When I try to "Save X Configuration File", there is a pop up with the path and file name.  No matter how I save, either by merging with existing file or not checking that box; the result is the same.  I get an error message:

Unable to create New X Config backup file /etc/x11/xorg.conf.back

Any ideas on a work around.  I have to have dual monitors, and I don't want to reconfigure every time I log in.

thanks for the help.

---

### Post by Bakon Jarser on 2008-07-11
try launching nvidia-settings with root privaleges.

```
gksudo nvidia-settings
```

---

### Post by gdonwallace on 2008-07-14
I'll give that a shot and see what happens.

---

