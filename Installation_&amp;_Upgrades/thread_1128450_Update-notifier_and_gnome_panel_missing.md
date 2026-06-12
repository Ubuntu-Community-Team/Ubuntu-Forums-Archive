---
title: "Update-notifier and gnome panel missing"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by darramonde on 2009-04-17
I've recently upgraded to *Ubuntu 9.04*. At first it ran perfectly, but now it seems like the **gnome panel** and the **update-notifier** have gone missing.

I've installed the gnome panel and updated by using the terminal but still; a black screen is all there is. Where are all my folders and programs?

At log in there's a message: *"your PnPBIOS caused fatal error"*...*"you may need to reboot with pnpbios=off to operate stable"*. Are these problems interrelated and in that case, how do I change the pnpbios?

---

### Post by nolanjurgens on 2009-04-17
I'm having the same issue. gnome-panel seems to run fine when started from the terminal and from a session startup entry I made for it, but it doesn't start up on it's own normally. I just upgraded to Jaunty as well.

Someone else had this issue with an upgrade to Intrepid as well.
[Same issue on Intrepid upgrade]("http://ubuntuforums.org/showthread.php?t=1127777&highlight=gnome-panel")

---

### Post by nolanjurgens on 2009-04-18
I just ran across the 9.04 release notes. Seems they changed the behavior of the update-notifier. Maybe that's what's happening? If you want the old behavior run:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```
[9.04 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/904")

Just noticed the mention of PnP BIOS settings. That's gonna vary by BIOS on how you change it, but if you go into your BIOS setup you should see some mention of Plug and Play OS, or something of the sort, if you can disable it.

---

