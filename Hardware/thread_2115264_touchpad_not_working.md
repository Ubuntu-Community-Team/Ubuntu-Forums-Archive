---
title: "touchpad not working"
date: 2013-02-12
forum: Hardware
---

### Post by rimzai on 2013-02-12
hey guys,

got a prbl with my touchpad since i upgraded to 12.04 : its working but i cant do nothing with it : very imprecise and very slow.

try to handle the touchpad config in settings but no results...

well this is not a big issue since the mouse is working properly (even its a very recent microsoft model), but well i would be happy to have a portable entire portable ^^

technically
xinput in terminal returns :
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Comfort Mouse 6000                id=9    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

(see the microsoft deluxe mouse)

and i guess alpsPS2 is the touchpad ?? so WTF :D

also i read somewhere else that xserver-xorg-input-synaptics should be installed, which it is but xserver-xorg-input-synaptics-quantal is not (anyone can tell me the difference ??)

thx for posts and comments
rimzai

dell inspiron 6000, ubuntu 12.04 lts, 32 bit
long life to prehistorical computers, lets save the planet

---

