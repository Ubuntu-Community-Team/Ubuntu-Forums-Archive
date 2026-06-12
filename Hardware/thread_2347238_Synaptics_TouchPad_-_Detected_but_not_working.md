---
title: "Synaptics TouchPad - Detected but not working"
date: 2016-12-22
forum: Hardware
---

### Post by cname2 on 2016-12-22
I'm using an Acer Swift 7 which works perfectly apart from the touchpad. The touchpad is recognized and configurable via System Settings, but doesn't respond to any clicks or movement.

```

$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)

```

I have tried 16.04.1 and 16.10 with all updates applied. I reviewed the community troubleshooting guide but didn't find anything that applied.

Can anyone point me to some troubleshooting steps? Thanks in advance

---

### Post by cname2 on 2016-12-22
Fixed by doing the following:

- Re-install Windows 10 using a bootable USB
- Installed Windows touchpad driver from Acer (this is possibly an un-related step, link below)
- Updated BIOS 

Driver and BIOS can be retrieved from here: [https://www.acer.com/ac/en/US/content/support-product/6958?b=1](https://www.acer.com/ac/en/US/content/support-product/6958?b=1)

Restarted using Ubuntu 16.04.1 live-USB and touchpad works perfectly. Continued with installation as normal, everything works.

---

