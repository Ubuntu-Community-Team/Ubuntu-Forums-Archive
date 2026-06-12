---
title: "Elan Touchpad not Recognized after 4.2.0-30 update"
date: 2016-02-23
forum: Hardware
---

### Post by mrmuffin0 on 2016-02-23
Hi all,

First off, apologies if this is in the wrong section. 
I'm writing on a Toshiba Chromebook 2, running Lubuntu 15.10. I recently updated from 4.2.0-27 to 4.2.0-30, and the touchpad doesn't seem to work.

From 4.2.0-27

```

xinput
&#9121; Virtual core pointer                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                               id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=12    [slave  keyboard (3)]

```

But running from 4.2.0-30, 

```

xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=11    [slave  keyboard (3)]

```

It seems that the Elan Touchpad isn't being recognized. Is there a driver that I'm missing? Or is there something with the update that changed something about the touchpad drivers?

Thanks in advanced.

---

### Post by tipesterseck on 2016-02-25
I have this exact same problem. 
Also, my sound stopped working, as did my ability to open the lid and resume from sleep. I'm guessing it's all connected somehow. Before the update everything had been working perfectly for several months.

---

### Post by tipesterseck on 2016-02-27
This bug has been reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1549354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1549354)
From what I understand, if we all confirm that the bug affects us there, there's a higher chance that the bug will get fixed.

---

### Post by irvine_himself2 on 2016-02-28
I updated everything a few day's ago without any problems. Here is my system for comparison

```
uname -r
4.2.0-30-lowlatency
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; E-Signal USB Gaming Mouse                   id=10    [slave  pointer  (2)]
&#9116;   &#8627; E-Signal USB Gaming Mouse                   id=11    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=15    [slave  keyboard (3)]
  
```

Not sure if it is relevant, but I also installed all of the available proprietary drivers hope this helps.

Irvine

---

### Post by Damienstenson on 2016-02-29
I'm in the same position. Moving from 4.2.0-27 to 4.2.0-30 did the damage. Hopefully it gets addressed soon.

---

### Post by X-RED_Tech on 2016-02-29
> **Damienstenson said:**
> I'm in the same position. Moving from 4.2.0-27 to 4.2.0-30 did the damage. Hopefully it gets addressed soon.

You can help by following the advice in post #3.

---

