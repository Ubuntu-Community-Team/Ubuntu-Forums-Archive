---
title: "Touchpad not detected on Ubuntu 22.04 LTS. Dell Inspiron 3543."
date: 2022-04-22
forum: Hardware
---

### Post by linzuxuan on 2022-04-22
Yesterday, I updated ubuntu from 20.04 to 22.04, then my touchpad not worked. This is some information on my machine:
```

> xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Wireless Keyboard PID:4023         id=15    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Wireless Mouse                     id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD: Integrate             id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                       id=14    [slave  keyboard (3)]
    &#8627; Logitech Wireless Keyboard PID:4023         id=16    [slave  keyboard (3)]

```
I need help because I really rely on the touchpad. Thanks for all.

---

### Post by linzuxuan on 2022-04-22
I found it's the problem of loose cable. Now I fixed it. Everything works fine.

---

