---
title: "PCManFM won't mount usb device"
date: 2008-09-04
forum: General Help
---

### Post by mp035 on 2008-09-04
Hi All,
I'm playing with a featherweight ubuntu for my eeepc using fluxbox and X on top of JEOS. (No Gnome or KDE)

I recently upgraded PCmanFM from 0.3.? to version 0.4.3 and now I get the following message box when I try to mount removable media:
> A security policy prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")

I downloaded version 0.5 from getdeb, and tried that, but still have the same problem.

I've searched everywhere.  BTW My user is already a member of the "plugdev" group.

Any help is appreciated.

---

### Post by Thanoulis on 2008-09-04
I believe that is the hal that causes that. PCManFM has compiled with hal support.You can try to install the non-hal version (its in repositories), or you can compile your own (which i recommend).

---

### Post by mp035 on 2008-09-04
Just tried pcmanfm-nohal from the repositories, the nohal version will not mount media at all.

Further info: The hal version mounted media as root, but displayed that message when started as normal user.

---

### Post by mp035 on 2008-09-05
Ok, I gave up.  I now use a combination of rox-filer and ivman, it seems to work well.

If anyone comes across this thread and knows a solution, please post to it, I will keep checking it periodically.

Thanks.

---

### Post by zkeng on 2008-10-27
Have you installed:

pmount

It gives normal user permission to mount removable devices.

---

