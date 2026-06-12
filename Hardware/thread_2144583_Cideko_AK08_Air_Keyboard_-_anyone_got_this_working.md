---
title: "Cideko AK08 Air Keyboard - anyone got this working?"
date: 2013-05-12
forum: Hardware
---

### Post by Fynn on 2013-05-12
Has anyone managed to get a Cideko AK08 Air Keyboard working under Ubuntu?  Mine is showing up under Settings > Mouse and Touchpad, but doesn't seem to do anything.

---

### Post by MrBackhand on 2013-06-02
I can confirm the Cideko AK08 Air Keyboard Conqueror works under Mythbuntu 12.04 right out of the box.  The keyboard works without any additional configuration but the joysticks and pad will require joystick installed.  Mame worked perfectly with the Cideko.  I have not been able to configure MythTV so the joysticks works but the arrow keys on the keypad do.  I have not tried to program the D1-D4 keys yet so I do not know if they work.  I hope this helps!

---

### Post by Fynn on 2013-07-01
I've just come back to this after some time away and thought I'd break out the Cideko again.  If I open a terminal to the Ubuntu box on my laptop and type ```
cat /dev/input/event13
``` I get a load of random text in my PuTTY window and the Cideko starts to work.  When I exit the command, all fails again.

Can anyone help diagnose where the problem lies?  Is this a lirc issue maybe?

---

### Post by z7APXKm on 2013-10-24
[http://ubuntuforums.org/showthread.php?t=2170304](http://ubuntuforums.org/showthread.php?t=2170304) was the solution.

---

