---
title: "Long pause to get shutdown dialog."
date: 2008-11-25
forum: General Help
---

### Post by Jumphog on 2008-11-25
Fresh install & update of Intrepid on an Acer Aspire One, with tweaks as described on [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L) , also suspend and hibernate disabled through gconf-editor.

When I try to get to the shutdown dialog either through the menus or by pressing the power button there is a 30-50 second pause before the dialog box shows. During roughly the first half of the pause the panel is unresponsive but will queue up any buffered clicks and eventually act on them all in one go. When the dialog does appear, shutdown and restart work fine.

Anyone else have this issue or any ideas?

---

### Post by arrange on 2008-11-25
Check if you have an instance of "gnome-power-manager" running (f.e. in System - Administration - System Monitor). If not, enable it (f.e. by Alt-F2 and typing "gnome-power-manager" into it). Then try shutting down again.

---

### Post by Jumphog on 2008-11-25
Thanks for the reply. Ive just turned the machine on again and gnome-power-manager is running. This time there is no delay in getting the dialog box up. If it happens again I will check to see whats running. A bit odd as when I was trying to pin down what was happening I rebooted and power cycled a dozen or so times and it was always slow...

---

### Post by Jumphog on 2008-11-28
Happened again yesterday, but the pause was more like 2 minutes. I check for gnome-power-manager and it was running...

---

### Post by 3rdalbum on 2008-11-28
Try turning on suspend and hibernate in gconf-editor? I didn't have the problem on my Aspire One when I was running plain Ubuntu, and I don't have the problem with the Netbook interface.

---

### Post by maxpathan on 2009-05-17
Hi
I've got 8.04 on my desktop and its been fine, but since last week I'm also suffering from this :-(

However it is only my userid. If I use a different user id, that doesnt seem to suffer from this.

ANy ideas what the cause is. I checked the power managerment process and that is running (sleep mode)


Regards
Max


FIXED!!!

The power manager daemon was unticked. 
SYSTEM > PREFERENCES > SESSIONS > STARTUP PROGRAMS. Scroll down and tick Power Manager

:-)

---

