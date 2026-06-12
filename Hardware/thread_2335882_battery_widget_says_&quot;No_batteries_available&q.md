---
title: "battery widget says &quot;No batteries available&quot;, works elsewhere"
date: 2016-09-02
forum: Hardware
---

### Post by Graeme_Pietersz on 2016-09-02
The plasma battery widgets and the system tray power manager icon both fail to show battery level, and, when hovered over, say "No batteries available". The icon does change to show when the laptop is plugged in.

[LIST]
[*]upower -d works
[*]when the screen is locked the battery level and charging state is shown
[*]the power manager dims the screen on low battery in line with the settings
[/LIST]
So the lower level stuff works, the screen locker can get the info, but the widget does not. I do not know what I need to look at to debug this.

---

### Post by howefield on 2016-09-02
Thread moved to the "*Hardware*" forum.

---

### Post by Graeme_Pietersz on 2016-09-02
Is this a hardware issue? It seems to be KDE specific. upower works, the XFCE battery monitor works, the KDE screen locker works. It looks to me very much a KDE issue.

---

### Post by Graeme_Pietersz on 2016-09-02
It worked correctly after reboot, did not work after next reboot, then worked again after login and logout without reboot.

---

### Post by J_Me on 2016-09-03
I think your issue is a bug in KDE.
Sometimes when my laptop is plugged into the power supply I get issues with the battery icon repeatedly switching between charging and fully charged which never seems to stop. The solution for me is to let the battery drain below 40% before plugging in the power cable.

---

### Post by Graeme_Pietersz on 2016-09-10
I am sure it is a KDE bug - that is why I originally posted in the KDE forum.

I did not get that behaviour. However, a few reboots later it seems to have fixed it self.

I did find some people with problems with KDE, which were solved by deleting the applet config. I think this is something similar and probably got fixed by changes in settings. No idea what changes!

---

### Post by Graeme_Pietersz on 2016-09-15
I recurs every few reboots/logins. Everything other than the widget seems to get the battery life right.

Thanks whoever moved this back to the Kubuntu Forum

---

