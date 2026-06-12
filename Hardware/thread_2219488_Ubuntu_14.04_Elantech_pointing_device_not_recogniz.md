---
title: "Ubuntu 14.04 Elantech pointing device not recognized"
date: 2014-04-24
forum: Hardware
---

### Post by tommaso-proietti-88 on 2014-04-24
Hi everyone,
I have just installed Ubuntu 14.04 on my laptop but the Elantech pointing device doesn't work at all. I have looked online for solutions, but nothing seems to work. The weird thing is that during the live test, everything was working out! 

This is the output of *xinput* command:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=9    [slave  keyboard (3)]
    &#8627; Power Button                                id=10    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

Hope somebody has an idea about how to fix it! 
Thanks! :)

---

### Post by tommaso-proietti-88 on 2014-04-24
If it can help, my laptop is a Gigabyte P34!

---

### Post by tommaso-proietti-88 on 2014-04-25
So it seems that formatting and reinstalling the OS, now everything works. No idea why it didn't before...

Thanks to everyone! :)

---

