---
title: "Keyboard preferences lost on automatic login"
date: 2008-09-26
forum: General Help
---

### Post by Colin@oxford on 2008-09-26
If I use "automatic login", so that I don't see the login screen, I notice that my keyboard preferences are lost on reboot.  Originally I found that the keyboard kept reverting to "us" - I solved this by putting "uk" into /usr/X11/xorg.conf .  I notice now that the arrows on the numeric keypad do not work after such a reboot.  In both instances the information in the Preferences->Keyboard box were as I had set them, not reflecting the action of the keyboard.  Setting to a different value and resetting to the required one always fixes it.

Any ideas on why this is happening, or how to get auto login to work correctly?

---

### Post by Colin@oxford on 2008-09-26
After the latest reboot (with non-automatic login) the keyboard preferences are still lost.  If I log out and log back in again, all appears to be OK.  Very strange.  Any ideas?

---

### Post by prshah on 2008-09-26
> **Colin@oxford said:**
> After the latest reboot (with non-automatic login) the keyboard preferences are still lost.  If I log out and log back in again, all appears to be OK.  Very strange.  Any ideas?

See any of these links: 

[[SOLVED] keyboard layout disappears on boot]("http://ubuntuforums.org/showthread.php?t=850040&highlight=setxkbmap")
[[SOLVED] Keyboard Layout Settings won't stick after reboot]("http://ubuntuforums.org/showthread.php?t=813567&highlight=setxkbmap")
[[SOLVED] Keyboar layout keeps resetting to US]("http://ubuntuforums.org/showthread.php?t=898384&highlight=setxkbmap")

Summary: Add "setxkbmap" to your startup sessions.

---

