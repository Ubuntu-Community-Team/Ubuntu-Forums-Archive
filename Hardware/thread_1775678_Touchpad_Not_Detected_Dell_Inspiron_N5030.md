---
title: "Touchpad Not Detected Dell Inspiron N5030"
date: 2011-06-05
forum: Hardware
---

### Post by christopher2405 on 2011-06-05
I have a Dell Inspiron N5030, and the touchpad is just detected as a generic mouse, meaning that I can't use the "configure touchpad" application.

Strangely, though, I can still use it to scroll, I just can't configure it.

Do I need to update a driver, or do some manual configuration?

Thanks.

---

### Post by Zorael on 2011-06-05
What does it detect it as? Just "PS/2 Mouse"?

'**xinput list**' lists currently attached (and virtual) input devices.
```
$ **xinput list**
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; **SynPS/2 Synaptics TouchPad**                id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                            id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]
```

---

