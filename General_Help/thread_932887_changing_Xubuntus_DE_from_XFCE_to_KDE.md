---
title: "changing Xubuntus DE from XFCE to KDE"
date: 2008-09-28
forum: General Help
---

### Post by Aesculaius on 2008-09-28
Hi! Yes I know it sounds stupid.. but I couldnt download kubuntu or kubuntu kde4.. the download kept timing out.. So instead.. can I change xubuntus DE from XFCE4 to KDE4?

---

### Post by shaggy999 on 2008-09-29
You are in luck. The entire Kubuntu setup is a single metapackage you can install called 'kubuntu-desktop'. Afterwards you can remove xfce if you want by removing the 'xubuntu-desktop' package along with all dependencies.

So:

sudo apt-get install kubuntu-desktop

*reboot*

sudo apt-get autoremove xubuntu-desktop

---

### Post by shaggy999 on 2008-09-29
BTW, it's perfectily fine if you leave xubuntu-desktop installed. To switch between you can log out and at the login screen you can change sessions.

---

### Post by Aesculaius on 2008-09-29
Alright! Thanks.. now justone other question... After I do that, if i logged in as root and changed my /etc/rc.conf file so kdm is enabled as my Login manager and if I edit .xinitrc so that XFCE is disabled, Xubuntu will default into KDE correct?

---

### Post by snowpine on 2008-09-29
> **Aesculaius said:**
> Alright! Thanks.. now justone other question... After I do that, if i logged in as root and changed my /etc/rc.conf file so kdm is enabled as my Login manager and if I edit .xinitrc so that XFCE is disabled, Xubuntu will default into KDE correct?

No, that would be unnecessary. You can simply select KDE from the Sessions menu on your login screen. It will ask you if you want to make KDE the default.

---

### Post by Aesculaius on 2008-09-29
Oh ok lol sorry. Im still running in Arch Mode.. About a few days ago downloaded Arch and set that behemoth up on my Mac using Virtual Box. Dad wont let me set it up on said PC with Xubuntu since if I screw up.. Windows goes bye bye (who would cry about that seriously..) so Im going the safe route and using Wubi for the "Ubuntu" Family Linux Distros.. Thanks for ur help!

---

