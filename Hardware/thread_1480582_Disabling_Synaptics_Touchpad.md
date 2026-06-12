---
title: "Disabling Synaptics Touchpad"
date: 2010-05-11
forum: Hardware
---

### Post by kei-clone on 2010-05-11
Searched the forum for similar threads to this, everything I've found is out of date, usually 3 years old. xorg.conf no longer exists as it did in 2007, so asking for help again.

Currently working on an HP G70, I'd like to disable my touchpad since I'm using a mouse and typing can be quite annoying with it on. The disable button doesn't work, nor does System>Preferences>Mouse>Disable Touchpad When Typing.

Any advice?

---

### Post by ziekfiguur on 2010-05-13
I use a simple touchpad_switch script that can turn on and off my touchpad, here it is:
```

#!/usr/bin/env python

import subprocess

device = 'AlpsPS/2 ALPS GlidePoint'

def getvalue():
    proc = subprocess.Popen(['xinput', 'list-props', device], stdout=subprocess.PIPE)
    output = proc.stdout.readlines()
    for l in output:
        if l.find('Device Enabled') != -1:
            return int(l.split()[-1])
    return None

def main():
    value = getvalue()
    if value != None:
        subprocess.Popen(['xinput', 'set-int-prop', device, 'Device Enabled', '8', str(int(not value))])

if __name__ == '__main__':
    main()

```
Replace the 'AlpsPS/2 ALPS GlidePoint' with the device name of your thouchpad (You can find it with `$xinput list'.), and place the file in /usr/bin/ or something.
Then go to System > preferences > keyboard shortkeys
click `add' and type `touchpad_switch' as command and choose a suitable hotkey (i use the windows key + F2)

Good Luck.

---

### Post by Kung! on 2010-05-16
I don't know if this will help at all; but I literally just discovered something about an hour ago.

In the same window under the "Disable touchpad" option there's also an option saying something like "Disable click ability on touch pad."  It essentially disables the ability to use the touchpad like a mouse - which I RARELY use anyways.

I tried EVERYTHING else...and evidently my light touches on the touchpad were enough to double-click and such, which was causing the problem.  Disabling it as a 'clicker' removed the problem for me.  :)

---

