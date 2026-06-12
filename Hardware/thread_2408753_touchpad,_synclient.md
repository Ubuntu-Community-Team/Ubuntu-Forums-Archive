---
title: "touchpad, synclient"
date: 2018-12-22
forum: Hardware
---

### Post by bradhaack on 2018-12-22
I installed lubuntu and I was using synclient to enable and disable the touchpad.    I am now using the xcfe desktop (on the lubuntu install) and cannot control the touchpad with synclient.   
if I run
```
synclient touchpadoff=1
```
and I set up a shortcut key with
```
synclient TouchpadOff=$(synclient -l | grep -c 'TouchpadOff.*=.*0')
```
The touchpad is turned off briefly, but then comes back on.   
I can enable and disable it with Settings->Mouse and Touchpad, but if I disable it and don't have the mouse I can't enable it.     I'm guessing that there is a different driver in control.    It would be nice if there was a way to detect the mouse and disable the touchpad, else if not mouse then use the touchpad.

---

### Post by ajgreeny on 2018-12-22
Try using the **Keyboard -> shortcuts** utility in Xubuntu settings manager with your choice of shortcut (eg **Winkey+T** for ease or remembering it) and point that shortcut to the command **synclient touchpadoff=1** and a different shortcut (eg Alt+T) for command **synclient thoucpadoff=0**

That should allow you to turn the touchpad on or off at will using the keyboard alone with no need for any other application running.

---

### Post by bradhaack on 2018-12-22
I guess I wasn't clear,   the synclient cmds only work for a couple of seconds, then the touchpad reverts to the setting in 'mouse and touchpad'

---

