---
title: "Problems with iMON/lirc"
date: 2011-07-12
forum: Hardware
---

### Post by wicht on 2011-07-12
Hello!

I have tried several days to get this iMON working in Natty, but it does not look like I will manage that... let me explain the problem.
My receiver is a SoundGraph iMON with a VFD display, lsusb says:
> Bus 002 Device 003: ID 15c2:0036 SoundGraph Inc. LC16M VFD Display/IR Receiver
I think that all required modules are loaded, because I enabled the option "debug=1" for the imon module, and everytime I press any button, /var/log/syslog reflects my keypress.
Running > ir-keytable -c -p rc-6 -w /lib/udev/rc_keymaps/imon_mce -t gives output for every key, it looks like this:

> 1310495083.859494: event MSC: scancode = 200004f
1310495083.963502: event key up: KEY_RIGHT (0x006a)
1310495083.963504: event sync
1310495084.523488: event MSC: scancode = 200001e
1310495084.523492: event key down: KEY_NUMERIC_1 (0x0201)
1310495084.523493: event sync
1310495084.619497: event MSC: scancode = 200001e
1310495084.715491: event key up: KEY_NUMERIC_1 (0x0201)
1310495084.715493: event sync
1310495085.003494: event MSC: scancode = 200001f
1310495085.003498: event key down: KEY_NUMERIC_2 (0x0202)
1310495085.003499: event sync
1310495085.099494: event MSC: scancode = 200001f
1310495085.203503: event key up: KEY_NUMERIC_2 (0x0202)
1310495085.203505: event sync
1310495086.342489: event MSC: scancode = 800ff416
1310495086.454503: event MSC: scancode = 800ff416
1310495086.902497: event MSC: scancode = 800ff414
1310495087.006497: event MSC: scancode = 800ff414
1310495087.118493: event MSC: scancode = 800ff414

Everything seems to work, but those "event MSC:" things do not seem to be forwarded even if they are registered in the set keymap (/lib/udev/rc_keymaps/imon_mce). Only keys that have a "key up" and "key down" in the log above get forwarded, for example KEY_NUMERIC_2, so these "event MSC" keys are unuseable for me as it seems at the moment.

Is there any chance to get the "event MSCs" to something that gets "up" and "down" events?


I would really appreciate any help.. this seems to be the last problem getting my HTPC up and running  :(


Thanks in advance,

Alex

---

