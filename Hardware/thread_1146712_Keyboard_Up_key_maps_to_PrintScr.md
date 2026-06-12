---
title: "Keyboard Up key maps to PrintScr"
date: 2009-05-02
forum: Hardware
---

### Post by sequalit on 2009-05-02
I have a generic black unmarked ps/2 keyboard.

I was running Ubuntu 8.04 and I upgraded to 8.10 and then immediately upgraded from there to 9.04. Not sure if it broke during 8.10 or 9.04 since I did them back to back.

Whenever I press the UP arrow key, it comes up with gnome screen shot utility, and If i press ctrl+up it has a screenshot of the current active window. Other keys such as insert, delete, home, end, prtscr do not work.

I have searched and searched and have only turned up dead ends on a fix.

I do not have any InputDevice entry in my xorg.conf.

List of what has NOT worked:
*Adding "setxkbmap -keycodes evdev &" to ~/.xinitrc followed by a restart
*changed my keyboard model to "Evdev-managed keyboard
*gconftool2 --recursive-reset keyboard (not sure exactly what the command is)

Any help would be greatly appreciated!

---

### Post by pastalavista on 2009-05-02
Open System > Preferrences > Keyboard (have you tried this?) Click 'Layout' and then Keyboard Model. There are lots of options you can try. Hopefully you can find one that works right.

---

### Post by sequalit on 2009-05-02
Yes, I have tried all of the generic types, and even the microsoft types (since the only markings on this keyboard is that windows is a trademark of microsoft).

None of them worked.

I have also completely removed and reinstalled xserver-xorg-input, that did not work either.

---

