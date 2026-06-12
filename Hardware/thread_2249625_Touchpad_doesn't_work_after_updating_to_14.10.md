---
title: "Touchpad doesn't work after updating to 14.10"
date: 2014-10-23
forum: Hardware
---

### Post by jyrki-deneve on 2014-10-23
Hi,

I just updated from Ubuntu 14.04 to 14.10, but my touchpad doesn't work anymore.
I have a Dell XPS 13 Haswell laptopwith touchscreen. In 14.04 my touchpad worked fine, but the touchscreen(only clicking was possible) didn't work properly. In 14.10 the touchscreen works (it supports scroll and drag), but as you can see below the touchpad isn't detected. 

```

> xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SYNAPTICS Synaptics Large Touch Screen      id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                        id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=12    [slave  keyboard (3)]


```

I guess it has something to do with drivers, but I don't know where to start searching.

Thanks,
Jyrki

---

### Post by lesharris on 2014-10-23
Hi, I use the same machine and had the same problem.  In my case I had the i2c-hid module blacklisted because it used to cause some conflict with the touchpad and the touchscreen.   This is no longer the case and as soon as I stopped blacking the module the touchpad started working after a reboot (and the touchscreen still works as well).

Hope this helps.

---

### Post by jyrki-deneve on 2014-10-24
Thanks, removing the i2c-hid line from the blacklist config did the job!

---

### Post by martin-grenfell on 2014-10-27
I had the same issue and this fix worked for me too. Thanks!

---

