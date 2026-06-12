---
title: "Need Help"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by new_to_ubun2 on 2009-07-20
I installed ubuntu 8.10 using option install inside windows xp.
Hence after every time there was option screen coming which OS to be used, but now I've re-installed windows Xp and there is no such option screen coming up,What can be done now if I don't wanted to re-install ubuntu...help me...

---

### Post by doas777 on 2009-07-20
well all you need to do is reinstall grub off a livecd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by new_to_ubun2 on 2009-07-20
Thanks for help...
But I'm unable to understand how can I open terminal using live ubuntu cd please explain step by step if possible...

---

### Post by raymondh on 2009-07-20
> **new_to_ubun2 said:**
> I installed ubuntu 8.10 using option install inside windows xp.
Hence after every time there was option screen coming which OS to be used, **but now I've re-installed windows Xp** and there is no such option screen coming up,What can be done now if I don't wanted to re-install ubuntu...help me...

My thoughts:

Previously, when you installed Ubuntu thru WUBI, Ubuntu resided INSIDE your windows installation (as a file of windows).  Now, when you re-installed XP (see quote above), XP may/will overwrite everything..... including your Ubuntu install.

Quick check :  Do you still have your old files before the XP re-install?  Can you look at your file system and locate C:/Ubuntu and see if it's there?

If the answer is 'no' ... then the XP re-install overwrote/deleted C:/Ubuntu.  In this case, you need to re-install Ubuntu again.

If the answer is 'yes', then try to re-install/recover GRUB using the tutorial presented by doas777.

To use the terminal from the liveCD, boot into the liveCD and select "TRY WITHOUT ANY CHANGES TO YOUR SYSTEM". That is known as a live session.  From there, go to applications > accessories > terminal.

Back up your files first.

Good luck.

---

### Post by new_to_ubun2 on 2009-07-21
> **raymondhenson said:**
> My thoughts:

Previously, when you installed Ubuntu thru WUBI, Ubuntu resided INSIDE your windows installation (as a file of windows).  Now, when you re-installed XP (see quote above), XP may/will overwrite everything..... including your Ubuntu install.

Quick check :  Do you still have your old files before the XP re-install?  Can you look at your file system and locate C:/Ubuntu and see if it's there?

If the answer is 'no' ... then the XP re-install overwrote/deleted C:/Ubuntu.  In this case, you need to re-install Ubuntu again.

If the answer is 'yes', then try to re-install/recover GRUB using the tutorial presented by doas777.

To use the terminal from the liveCD, boot into the liveCD and select "TRY WITHOUT ANY CHANGES TO YOUR SYSTEM". That is known as a live session.  From there, go to applications > accessories > terminal.

Back up your files first.

Good luck.
thank you for help...
But I'm having new problem I'm unable to run live session the system is asking me to enter user name and password and when I tried to login with old user name and password it gives an error message what to do now...?

---

