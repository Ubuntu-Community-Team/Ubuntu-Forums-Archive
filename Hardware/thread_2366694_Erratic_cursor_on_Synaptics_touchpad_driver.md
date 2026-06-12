---
title: "Erratic cursor on Synaptics touchpad driver"
date: 2017-07-20
forum: Hardware
---

### Post by miqrojamie on 2017-07-20
Hi,
My Acer ES1-531 laptop has a Synaptics touchpad driver and it acts extremely erratic after about an hour of use or less.

Here's the logs from 'xinput list':

jamie@jamie-Aspire-ES1-531:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SYN1B7F:00 06CB:7406 Touchpad               id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; VGA Webcam                                  id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys       

Apparently this is a known bug, but hasn't been fixed. The same problems actually happen in Windows when I had it installed, too.
Could anyone guide me on how to fix it? Thanks!

---

