---
title: "After Upgrade to 14.10 touchscreen isn't working"
date: 2014-10-23
forum: Hardware
---

### Post by zottelmann-h on 2014-10-23
Hello!

I just upgraded my Fujitsu Siemens lifebook t730 to 14.10. And sadly the touchscreen stopped working and the system say it finds no wacom device (on 14.04 everything worked so far).
here is my xinput:
xinput list
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9116;   &#8627; ALPS PS/2 Device                            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02E3                             id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02B1                             id=9    [slave  keyboard (3)]
    &#8627; Fujitsu FUJ02BF                             id=10    [slave  keyboard (3)]
    &#8627; Power Button                                id=11    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```
anybody knows what to do?

furthermore the command xsetwacon list device shows no result

---

### Post by zottelmann-h on 2014-10-26
Well, after going back to 14.04 everything works normal again. Sometimes the newest Software isnt the best.

---

### Post by ericscott07 on 2014-12-08
I'm having the same problem with my t730.

---

