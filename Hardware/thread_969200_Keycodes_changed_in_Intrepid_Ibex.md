---
title: "Keycodes changed in Intrepid Ibex"
date: 2008-11-03
forum: Hardware
---

### Post by Jenda on 2008-11-03
I found this thread: [http://ubuntuforums.org/showthread.php?t=943160&highlight=keycodes+intrepid](http://ubuntuforums.org/showthread.php?t=943160&highlight=keycodes+intrepid)

I have the same problem. The author already solved his, described it, but didn't post a solution of any kind.
Anyone have a clue?

BTW, the most annoying part is that the up arrow key became "print screen", and I can't even seem to get its keycode with xev.

Thanks &#12484;

---

### Post by Jenda on 2008-11-18
I still haven't had any luck with this... so *bump* :)

---

### Post by cdtech on 2008-11-18
Make sure you have the keyboard model as Generic Evdev-managed keyboard in System > Preferences > Keyboard, in the tab layouts.

This worked for me...

**UPDATE::.**
The "/etc/X11/xorg.conf" configuration file still has InputDevice entries for the mouse and keyboard, but they are ignored because input-hotplug is used instead. The keyboard settings come from "/etc/default/console-setup", and in order to change them you need to use the command "sudo dpkg-reconfigure console-setup". Once you do the configuration, you'll need to logout and back in.

---

### Post by Jenda on 2008-11-18
thanks, CDtech, but it doesn't seem to help, even after rebooting. For example, my up key still xev's as an up key, but with shift, it becomes "sysreq" :D

---

