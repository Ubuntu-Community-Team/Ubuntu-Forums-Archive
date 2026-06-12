---
title: "Gaming Mouse not Working/Mousing"
date: 2013-09-02
forum: Hardware
---

### Post by theste1234 on 2013-09-02
I am having a bit of a problem with my gaming mouse ([Leetgion Hellion]("http://www.leetgion.com/products.php")) that works fine in windows. I have just installed Ubuntu 13.10 (32bit) and the mouse just does not respond in any way.

  
I have run xinput and is for some reson under the keyboard settings.

```

$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; CM Storm Trigger gaming Keyboard            id=9    [slave  pointer  (2)]
&#9116;   &#8627; MLK AGK 2.4G optical combo                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; CM Storm Trigger gaming Keyboard            id=8    [slave  keyboard (3)]
    &#8627; Holtek USB Gaming Mouse                     id=10    [slave  keyboard (3)]
    &#8627; MLK AGK 2.4G optical combo                  id=11    [slave  keyboard (3)]

```

when I type in xinput get-button-map 10 i get this 

```

xinput get-button-map 10
device has no buttons

```

Any help will be appreciated, I am really stuck :(.

---

### Post by ablacksheep on 2013-10-02
could you give me the output of the following commands?

`uname -a`

`lsusb`

`tree /sys/bus/usb`

---

