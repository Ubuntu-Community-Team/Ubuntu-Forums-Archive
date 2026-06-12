---
title: "How to disable the touchpad, whether or not I'm typing."
date: 2015-12-22
forum: Hardware
---

### Post by Keiva on 2015-12-22
I have a Dell Inspiron 1550, and would like to be able to completely disable my touchpad when I plug in the mouse.  Or rather, I want to be able to enable it on the few occasions when I don't use a mouse.

This post is similar to what I'm looking for, but I don't need an application.  A terminal command is preferable.
[http://ubuntuforums.org/showthread.php?t=2287479&highlight=configure+touchpad](http://ubuntuforums.org/showthread.php?t=2287479&highlight=configure+touchpad)

Is there a command that quickly enables/disables the touchpad, or do I need to go through xorg.conf?

Tyvm!
K

---

### Post by kc1di on 2015-12-22
you can try this command```
synclient TouchPadOff=1
```  if that works you can re-enable it when you want to with the following command
```
synclient TouchPadOff=0
```

good luck

---

### Post by sudodus on 2015-12-22
```
synclient TouchPadOff={1 or 0}
``` works in Lubuntu and Xubuntu. I use it often.

But if you use standard Ubuntu with Unity, there is a GUI application that overrides synclient. Use the icon with tools 'System Settings', select 'Mouse and Touchpad' and click on the switch to 'OFF'. Then the touchpad will be turned off. Click again and it will be turned 'ON'.

---

### Post by vasa1 on 2015-12-22
And here's code for a toggle thanks to **yetimon_64**:
```
#!/bin/sh

TOGGLE=$HOME/.toggle

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    synclient TouchPadOff=1 &
else
    rm $TOGGLE
    synclient TouchPadOff=0 &
fi

exit 0
```

---

