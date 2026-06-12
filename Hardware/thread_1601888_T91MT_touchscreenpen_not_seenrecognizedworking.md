---
title: "T91MT touchscreen/pen not seen/recognized/working"
date: 2010-10-20
forum: Hardware
---

### Post by jamoozy on 2010-10-20
Hi.  I just got an ASUS T91TM Eee PC (from that woot.com deal a couple  weeks back), and found that the multitouch/pen surface does not work  out-of-the box with 10.10 netbook edition.  In fact, xinput doesn't even  see it.

```
$ xinput list
&#9121; Virtual core pointer                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11   [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=8    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10   [slave  keyboard (3)]
```

Resultantly  I'm just running GNOME instead  of unity ... I was really looking forward to trying it out on a table,  too ... :sad:

This thread seems to have a lot of relevant stuff in it:
[http://ubuntuforums.org/showthread.php?t=1468376&highlight=t101tm](http://ubuntuforums.org/showthread.php?t=1468376&highlight=t101tm)
but I haven't been able to get anything to work on my machine.

I'm  not a kernel hacker at all (not sure what's going on in that thing),  but I get the feeling that since the T101TM and my T91TM are HID devices  made by the same company that perform the same task, they probably have  very similar (identical?) interfaces.  My thought was "What if I just  told the T101TM driver to pretend my T91TM device is a T101TM?"  Would  this work?  How would I even go about doing that?

Anyway, just a  guess there.  An expert opinion would be greatly appreciated.  I'm  pretty familiar with Ubuntu, been using it for several years on several  machines.

Also, sleep/hibernate doesn't work either ... one step  at a time, I suppose.  I think I saw something about that in a different  thread (on the T101TM again), so maybe I'll look deeper into that  myself, but again an expert opinion would be great.

---

### Post by H3g3m0n on 2010-10-27
There is a guide here:
[http://ubuntuforums.org/showthread.php?t=1507489](http://ubuntuforums.org/showthread.php?t=1507489)

And another one here:
[http://ubuntuforums.org/showthread.php?t=1595220&highlight=t91mt](http://ubuntuforums.org/showthread.php?t=1595220&highlight=t91mt)

You won't get multitouch though, just single touch.

---

