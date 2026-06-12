---
title: "Touchscreen no longer recognised in 12.04"
date: 2012-05-07
forum: Hardware
---

### Post by Paddy Landau on 2012-05-07
In Natty 11.04, the touchscreen was recognised and I could use it.
```
[COLOR=Blue]$ xinput --list[/COLOR]
&#9121; Virtual core pointer                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Lite-On Technology Corp. Wireless Device    id=11   [slave  pointer  (2)]
&#9116;   &#8627; Lite-On Technology Corp. Wireless Device    id=12   [slave  pointer  (2)]
&#9116;   &#8627; **Quanta Computer OpticalTouchScreen**     id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; CNFA257                                     id=8    [slave  keyboard (3)]
    &#8627; Lite-On Technology Corp. Wireless Device    id=10    [slave  keyboard (3)]
```However, in Precise 12.04 (fresh installation, fully updated), it is no longer recognised.
```
[COLOR=Blue]$ xinput --list[/COLOR]
&#9121; Virtual core pointer                            id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                           id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; CNFA257                                     id=8    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                       id=9    [slave  keyboard (3)]
```I notice that it also doesn't see the wireless, but the wireless does work, so that may be a red herring.

Jockey does not report any additional proprietary drivers.

How can I get my touchscreen working again?

---

### Post by Paddy Landau on 2012-05-08
Bump?

---

### Post by toddvarg on 2012-05-13
I have the same problem, and it's a semi solution here, bur you only get one finger tap and not two finger. I'm still using ubuntu 11.10, it's working all the way.
[http://askubuntu.com/questions/129448/touch-screen-not-working-on-an-hp-touch-smart-610]("http://askubuntu.com/questions/129448/touch-screen-not-working-on-an-hp-touch-smart-610")

---

### Post by Paddy Landau on 2012-05-13
Thank you. My problem is related, but not quite identical.

I have since found further information, and have [raised a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/998546") and submitted to [ENAC]("http://lii-enac.fr/en/architecture/linux-input/multitouch-howto.html#report").

I have an [associated question on Ask Ubuntu]("http://askubuntu.com/questions/134505/touchscreen-broken-after-installing-12-04").

---

