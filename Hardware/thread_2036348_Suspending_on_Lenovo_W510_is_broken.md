---
title: "Suspending on Lenovo W510 is broken"
date: 2012-08-01
forum: Hardware
---

### Post by JessieAMorris on 2012-08-01
Hey all,

Recently I upgraded the HDD in my laptop to an SSD. I copied all the files over and then proceeded to install grub on my SSD. I then started experimenting with beta Nvidia drivers using the xorg edgers PPA, which broke my suspend/resume. I used the included ppa-purge tool (in xorg-edgers) to get rid of the beta drivers, but still a no go. I then tried to reinstall Ubuntu (then installed the Nvidia drivers), however my suspend/resume is still broken.

Attached is the /var/log/pm-suspend.log

I've checked to see if the xhci module is loaded (it isn't) and I've tried disabling wifi and other common problems.

Any thoughts/suggestions?

---

### Post by JessieAMorris on 2012-08-02
Bump.

---

