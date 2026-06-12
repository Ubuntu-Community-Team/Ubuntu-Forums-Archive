---
title: "KBlueLock appears on startup, how to stop it"
date: 2008-11-14
forum: General Help
---

### Post by sl33p3r on 2008-11-14
Ok, this is bugging me to hell. Lately, whenever i start my system (Kubuntu 8.04.1), a KBlueLock window appears. In the processes list it is stated as kbluelock -session 1022d19f1811ad000122667197300000071040041_1226694183_376399.
How can I get rid of it (without removing KBluetooth app from startup services)?
I have no idea why it started appearing in the first place, I certainly haven't checked or modified anything to enable this behavior.
Please help. Thank you.

---

### Post by sl33p3r on 2008-11-14
Nevermind, fixed it by adding kbluelock to "Apps to be excluded from sessions" in kcontrol's Session Manager tab. Although I find this to be an ugly fix, it works.
Could someone point me to a good tutorial on how sessions are handled in kde? I only find junk using google on this subject.
Thank you.

---

