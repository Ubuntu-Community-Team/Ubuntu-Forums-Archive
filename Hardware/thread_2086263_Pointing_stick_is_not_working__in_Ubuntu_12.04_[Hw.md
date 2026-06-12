---
title: "Pointing stick is not working  in Ubuntu 12.04 [H/w is Lenovo Thinkpad L430]"
date: 2012-11-20
forum: Hardware
---

### Post by akash mishra on 2012-11-20
I have got new lenovo Thikpad L430 & i have installled Ubutnu 12.04.
My pointing stick is not working , I tried a lot to fix but no luck. Below is the output of xinput:

xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera                           id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=12    [slave  keyboard (3)]

Can any one suggest how to detect/enable pointing stick in Ubuntu 12.04.

Cheers/Akash

---

### Post by kurt18947 on 2012-11-20
I assume you've looked at mouse & touchpad settings?  I'm using gnome-shell but I suspect Unity would be similar.  I just did the 'super' key and type 'mouse'.  A mouse settings app is among the choices.  My (older) Thinkpad shows both the touchpad and trackpoint.

---

### Post by linrunner on 2012-11-20
Hi,

this is a known problem with the L430/L530 models. As a workaround you may install the package **tp-trackpoint-elantech** from my PPA: [https://launchpad.net/~linrunner/+archive/thinkpad-extras](https://launchpad.net/~linrunner/+archive/thinkpad-extras)

_Please note:_ two-finger-scroll with the touchpad is not possible when the above workaround is used

---

### Post by lencho on 2013-04-03
Hello there,
Also affected with my L430.
I'm unable to fiddle with this machine too much (computer from my work!), but I did test a live CD of Ubuntu 11.10 after reading that the Trackpoint worked on this model with kernel 2.6.x and indeed it works... better. The Trackpoint in itself doesn't seem to react, but the trackpoint buttons work fine (they don't at all with 12.10).
So maybe there is a solution to be found in older kernels?
Don't know much about that so I'm afraid I can't help more, sadly.
Cheers,

---

