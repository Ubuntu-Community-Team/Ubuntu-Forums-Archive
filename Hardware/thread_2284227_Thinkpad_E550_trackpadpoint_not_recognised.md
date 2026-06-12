---
title: "Thinkpad E550 trackpad/point not recognised"
date: 2015-06-27
forum: Hardware
---

### Post by robhad on 2015-06-27
Hi everybody. I recently bought a Lenovo Thinkpad E550 and it's having a couple of issues when running Ubuntu (or any other distro for that matter) on it. The main one being that the trackpad and trackpoint are being recognised as a PS/2 Generic mouse. Output of xinput:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=11    [slave  keyboard (3)]
```

I'm not sure what to do. Because of this, I can't access settings to disable the trackpad when typing and other such related perks you'd expect to have when dealing with a Thinkpad. This makes it incredibly hard to type.

Any thoughts? I'm a newbie to linux so please be kind. I'm happy to report back with any information you might need to help me out. Thank you.

EDIT: I've resorted to using:

```
sudo modprobe -r psmouse
```

...but that's tedious and probably not the best way to go about making typing easier.

---

### Post by kalle6 on 2015-07-02
I have the same issue with my E550 and would be as thankful as robhad for useful advice!

---

