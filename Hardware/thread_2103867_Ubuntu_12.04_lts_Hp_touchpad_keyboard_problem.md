---
title: "Ubuntu 12.04 lts Hp touchpad keyboard problem"
date: 2013-01-11
forum: Hardware
---

### Post by tux-world on 2013-01-11
hi all. how to use keyboard or mouse usb for hp TP? i cant using hub usb.
can any body for help me?

---

### Post by tlhIngan on 2013-01-11
Are the USB ports enabled in the BIOS?

---

### Post by 1337_snic on 2013-01-11
Some more information is needed man. What version/distro are you running?  Have you tried plugging them in and seeing if they work? I know that 11.10 and up has issues with mouse and keyboards via usa, but it could be a BUNCH of different things. ):P

Edit: My bad didnt see in your title that you were running the latest lts.

Typically it is a simple fix for this.  I was able to create this error on 12.04 32-bit Where my mouse was not functioning. Keyboard i am unable to imitate. 

Terminal it up :)
```

xev

```
This will show you if your key strokes and mouse movements are being detected. If not try this.
```

xinput

```
For me returned this
```

elliott@elliott-desktop:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Mad Catz Mad Catz R.A.T.7 Mouse             id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; G19 Gaming Keyboard                         id=9    [slave  keyboard (3)]
    &#8627; G19 Gaming Keyboard                         id=10    [slave  keyboard (3)]
    &#8627; Logitech G19 Gaming Keyboard                id=11    [slave  keyboard (3)]


```

seeing that you can restart things from here. 
 example. To fix the mouse not working at all or onlyin being able to move and not click (left or right) i input
```

xinput reattach 8 2

```
where the first number is the device youd like to re attached and the second number is the master selection.
Hope i helped :)

---

### Post by tux-world on 2013-01-12
> **1337_snic said:**
> Some more information is needed man. What version/distro are you running?  Have you tried plugging them in and seeing if they work? I know that 11.10 and up has issues with mouse and keyboards via usa, but it could be a BUNCH of different things. ):P


thanks. but i want to use external keyboard on hp tablet toucpad with hub USB;)

---

