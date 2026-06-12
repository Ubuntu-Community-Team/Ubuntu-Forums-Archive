---
title: "Lenovo Z370 pressing OneKey Event blocks keyboard"
date: 2011-10-06
forum: Hardware
---

### Post by katastrophenschutzplan on 2011-10-06
Hello,

on the Lenovo Z370 on the right side above the keyboard there are five keys. I think the are called OneKey Events.
If I press one of the 3 left keys, they do what the should (sound up, down, mute). 
When pressing the 2 other ones nothing seems to happen.

But no matter which one I press afterwards the hole keyboard does not work anymore. Also the indicator-applet(?) lost its menus.

In the kern.log I found this:
```

kbd_keycode: 15 callbacks suppressed
keyboard: can't emulate rawmode for keycode 240
keyboard: can't emulate rawmode for keycode 240
keyboard: can't emulate rawmode for keycode 240
...

```I do not know, if those two things are related.

And in the file /usr/include/linux/input.h I found this line:
```
#define KEY_UNKNOWN             240
```
Maybe changing KEY_UNKNOWN would help, but I don not know what to write instead..

I am using Ubuntu 11.04 with Unity 3D.
```

uname -a
Linux c-Z370 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Any ideas, how I can prevent the blocking?
If there is anything you need to know, please let me know.

Thank you very much :)

---

### Post by senkovych on 2011-12-21
Look here: [http://blog.nexusger.de/?p=36](http://blog.nexusger.de/?p=36)

---

### Post by katastrophenschutzplan on 2011-12-22
Hello senkovych :)

> **senkovych said:**
> Look here: [http://blog.nexusger.de/?p=36](http://blog.nexusger.de/?p=36)
Thank you very much! I will try that as soon as possible (that would be in about one and a half week). :)

Have a nice day :)

---

### Post by phooky on 2012-01-28
This particular problem has been driving me nuts for a while, because just *brushing* the capacitive buttons can disable your keyboard. I just found a fix this afternoon. Add the following line to your /lib/udev/rules.d/95-keyboard-force-release.rules file:

```
ENV{DMI_VENDOR}=="LENOVO", ATTR{[dmi/id]product_name}=="IdeaPad Z370", RUN+="keyboard-force-release.sh $devpath common-volume-keys"
```

Additionally, if you accidentally lock up your keyboard this way, you can restore it by switching to a virtual terminal and then switching back to X (try Ctrl-Alt-F2 followed by Alt-F7).

---

### Post by katastrophenschutzplan on 2012-01-30
Hello :)

thank you very much! :)

Keyboard does not freeze anymore and the special-sound-keys are working.


 Have a nice day! :D

---

