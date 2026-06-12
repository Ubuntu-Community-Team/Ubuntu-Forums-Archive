---
title: "wacom stylus doesn't work after suspension"
date: 2015-05-10
forum: Hardware
---

### Post by dgtorpedo on 2015-05-10
Hi,
after suspension/resume my wacom stylus doesn't work any more.

xinput before suspension
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled Touchscreen stylus    id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Serial Penabled Touchscreen eraser    id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
    &#8627; Power Button                                id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

xinput after suspension
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
    &#8627; Power Button                                id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

I've tried the solution posted here: [https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/1275416](https://bugs.launchpad.net/ubuntu/+source/xinput/+bug/1275416) in #21 and #22, but it doesn't work for me.
Only logout/login reactivate the stylus (as described in #1).

I'm using xubuntu 14.04 with a LifeBook-T4220 and kernel 3.13.0-52-generic.

Any suggestion?

---

### Post by dgtorpedo on 2015-05-14
Solved using the #3 method posted here [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/807620](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/807620), that is:
Adding ```
SUSPEND_MODULES="wacom wacom_w8001"
``` to [FONT=courier new]/usr/lib/pm-utils/defaults
[/FONT]

---

### Post by dgtorpedo on 2015-05-18
The above solutions doesn't work any more (probably because I put my pc in suspend mode after a logout/login and not after a shutdown/start)!

Also, let me say that it's a bad practice to edit [FONT=courier new]/usr/lib/pm-utils/defaults[/FONT].
So, if you really need to change the variable [FONT=courier new]SUSPEND_MODULES[/FONT], create a file, called [FONT=courier new]modules[/FONT], in [FONT=courier new]/etc/pm/config.d/[/FONT] whith content:
```
SUSPEND_MODULES="wacom wacom_w8001"
```
The reference is the manual page of pm-utils [http://manpages.ubuntu.com/manpages/trusty/man8/pm-suspend.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/pm-suspend.8.html), which says that modules should be defined in /etc/pm/config.d/.
Furthermore, another good reference is this guide about loadable modules [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules).

But, even if I can unload the wacom modules before the suspension and even if the log file in [FONT=courier new]var/log/pm-suspend.log[/FONT] doesn't show any error, the stylus is still not recognized.

By trial and error this solution seems to work fine: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1251441/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1251441/comments/34)

---

