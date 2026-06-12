---
title: "Migrating to XFCE, Gnome services won't quit"
date: 2011-05-26
forum: Hardware
---

### Post by ashesh0326 on 2011-05-26
Hi, 

Ubuntu 11.04 with Unity didn't work out for me so I immediately switched to XFCE. Xubuntu is nice and the workflow is much better, though what bothers me is the Gnome services don't quit.

First of all, the power manager. The powermanager comes back up after every suspend - I've removed it from the Startup Programs list. So that causes my laptop to resume and immediately go back into suspend the moment it resumes. This happens due to calls to suspend to the Gnome power manager as well as the XFCE power manager. The question is how do I avoid gnome power manager from being invoked at all.

Secondly, the Gnome-screensaver. Whenever I resume from suspend/hibernate, I'm presented with the Gnome screensaver lock password dialog. I enter the password there, and the computer goes back into standby - due to the issue we discussed above. I need to stop Gnome-screensaver from being invoked as well.

I have to selectively deactivate gnome services because some of them, I need - e.g. the keyring service, which Adobe Air needs.

Thanks for reading through and I'll appreciate any help.

---

### Post by ashesh0326 on 2011-05-26
Bump. Anyone?

---

