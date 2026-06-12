---
title: "Strange Virtualbox problem"
date: 2008-05-30
forum: Hardware
---

### Post by Longrifle3006 on 2008-05-30
The Ubuntu install on my Toshiba laptop went smooth as silk, and I'm quite happy with everything, except...
I installed Virtualbox so that I may run Windows XP under Ubuntu. It's my understanding that this isn't uncommon around here. The Virtualbox install went smoothly, no problems. The problems start when I attempt the install of XP on the virtual machine. The disk boots fine on the virtual machine and the install begins normally. At some point during the install process my Toshiba simply shuts down as if the power was removed. When it happens I get no warning, no entries in the log file, nothing...just *poof* it's off. The most frustrating thing is that it never happens at the same point in the install process. I've tried the install at least a dozen times, and several times with different settings. I even deleted the virtual machine and set up a new one. Nothing seems to help.
I'm really at a loss here. Anybody have any ideas?

I *think* the model number of my Toshiba is A115-S129 but I don't have it with me at the moment to verify.

---

### Post by Vadi on 2008-05-30
I'd say post on VirtualBox forum for help, since it looks like it's a problem with their kernel module.

Additionally, where did you install Virtualbox from? If from Add/Remove, you can get an updated version at virtualbox.org. Just make sure to shutdown all your machines properly first, and uninstall virtualbox before upgrading.

---

### Post by Longrifle3006 on 2008-05-30
Update: it now appears that this is a hardware issue with the laptop, not a software issue. Consider it case closed....

---

