---
title: "how to enable touchpad on acer on start..."
date: 2013-06-15
forum: Hardware
---

### Post by whoever30 on 2013-06-15
Hi folks!

on every start of Ubuntu have to digit [Fn]+F7 to ENABLE touchpad!  [IMG]http://forums.linuxmint.com/images/smilies/icon_mad.gif[/IMG]  it does not happen on ubuntu 9.10 livecd or win 7...

acer aspire E1 32bit

[CODE$ xinput list
&#9121; Virtual core pointer                       id=2   [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                 id=4   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                         id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                      id=3   [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                id=5   [slave  keyboard (3)]
    &#8627; Power Button                               id=6   [slave  keyboard (3)]
    &#8627; Video Bus                                  id=7   [slave  keyboard (3)]
    &#8627; Power Button                               id=8   [slave  keyboard (3)]
    &#8627; Sleep Button                               id=9   [slave  keyboard (3)]
    &#8627; HD Webcam                                  id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard               id=11   [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                           id=13   [slave  keyboard (3)]][/CODE]

how to fix it?

tia!

---

### Post by whoever30 on 2013-06-15
no one?

---

### Post by whoever30 on 2013-06-16
...bump...

---

### Post by whoever30 on 2013-06-16
...up...

---

### Post by whoever30 on 2013-06-17
...&#8593;...

---

### Post by whoever30 on 2013-06-17
...:?:...

---

### Post by hansdown on 2013-06-18
Hi whoever30.

12.04 with kernel 3.2.0-27  would be a better choice.

I've seen posts that say it works better.

---

### Post by whoever30 on 2013-06-19
thx 4the reply dude!

but **K 3.2.0-27 **didn't help with [Fn]+F7 at start...

---

### Post by whoever30 on 2013-06-19
> **whoever30 said:**
>   it does not happen on ubuntu 9.10 livecd or win 7...

add **DSL** (damn small linux)  checked to the list that NO [Fn]+F7 to enable touchpad on start...

---

### Post by mörgæs on 2013-06-20
Please stop bumping your thread.

If you feel that you don't get enough answers this might help:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by whoever30 on 2013-06-20
this solution did the job:

```

echo "blacklist acer_wmi" | sudo tee /etc/modprobe.d/acer-wmi.conf
```

[http://ubuntuforums.org/showthread.php?t=2038917&page=2&p=12699437#post12699437](http://ubuntuforums.org/showthread.php?t=2038917&page=2&p=12699437#post12699437)

=D>

padlock around here

---

### Post by hansdown on 2013-06-20
Glad you fixed it, whoever30.

Good work.

---

