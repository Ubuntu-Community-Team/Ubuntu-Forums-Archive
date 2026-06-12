---
title: "No graphical interface on boot"
date: 2008-08-13
forum: General Help
---

### Post by perks on 2008-08-13
When I boot into Ubuntu 8.04 it says:
> kinit: name_to_dev_t (/dev/disk/by-uuid/574fc4d9-fd77-4524-8b2d-eb8bb73f4c10)=sda5(8,5)

kinit: trying to resume from (dev/disk)

kinit: No resume image, doing normal boot...

And then all I can do is login through terminal. Any help is appreciated! I'm using the LiveCD to post this.

---

### Post by prshah on 2008-08-13
> **perks said:**
> When I boot into Ubuntu 8.04 it says:
> kinit: name_to_dev_t (/dev/disk/by-uuid/574fc4d9-fd77-4524-8b2d-eb8bb73f4c10)=sda5(8,5)
kinit: trying to resume from (dev/disk)
kinit: No resume image, doing normal boot... 

And then all I can do is login through terminal. Any help is appreciated! I'm using the LiveCD to post this.


This is a normal message and has nothing to do with your problem. This message simply means that Ubuntu is looking for a resume image (eg., after hibernating), but since it doesn't find one, it's proceeding with normal boot rather than restoring hibernated information.

Simple things to try if you can't get into graphics mode:

1) Press Ctrl+Alt+F7 after system has started up (at the login prompt). If the screen goes blank and stays blank, press Ctrl+Alt+F1 to get back to text (command line) mode.

2) Login, then give the command```
startx
``` (Note: no "sudo"). If you still do not get a GUI, post back with outputs to the previous command, as well as the following```

tail /var/log/messages
tail /var/log/Xorg.0.log
```

Note case and numbers in the previous command carefully to avoid mistyping.

---

