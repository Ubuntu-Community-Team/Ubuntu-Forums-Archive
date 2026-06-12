---
title: "Open Office 3.0 vanishing quickstart solution"
date: 2008-11-12
forum: General Help
---

### Post by Arup on 2008-11-12
This is a small yet significant tip which I had to find after hours of installs and re-installs and hair tearing. After upgrading to OO 3.0, the quickstart icon wouldn't stay after a reboot, this problem has been discussed elsewhere as well but with no viable solution. What happens is the .config folder gets a broken link placed in it and on subsequent reboots, it vanishes. The trick to keeping the link right is to enable quickstart in the pre-installed 00 2.4, then install OO 3.0 over it and all the settings including the correct quick start link is preserved and no more vanishing issues after reboot.

For some this may be trivial but for daily OO users, quick start is quintessential even in Ubuntu where its much faster than in Windows, the quickstart makes it lightning fast to load, also its way more convenient than digging through menus to access various OO apps.

---

### Post by andreasis on 2008-12-02
I have not tested this, but I am aware that the quickstarter vanishes after restart.

OO Quickstarter is absolutely essential!  Can anyone else provide any input on this?

Who knows why this happens and how it can be solved a more logical way?

---

### Post by andreasis on 2008-12-05
bump?

---

### Post by andreasis on 2008-12-07
I've found a possible solution, but I need someone to test it.  The launchpad repo's don't seem to be available anymore, but for someone who's got oo3 with this problem, this might be worth a shot: ```
ooffice -quickstart -nologo -nodefault
```

---

### Post by spirit_of_life on 2009-01-16
Hello!

I just removed openoffice.org 2.4 and replaced it with 3.0 on my Ubuntu 8.04 installation, only to run into exactly the problem of the original post: I don't have a Quickstarter, and there is no option to turn it on in tools->options->memory. Was anyone able to solve this issue? I don't have ooffice 2.4 any more, so the other workarounds suggested on this forum so far do not work for me.

---

### Post by Arup on 2009-01-17
The quick start is retained when OO 3 is installed over OO 2.4, however recently there was some big updates to OO 3 from the launchpad and my quickstart has vanished for good unfortunately.

---

