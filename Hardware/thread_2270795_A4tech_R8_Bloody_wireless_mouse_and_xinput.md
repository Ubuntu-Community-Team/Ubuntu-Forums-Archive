---
title: "A4tech R8 Bloody wireless mouse and xinput"
date: 2015-03-25
forum: Hardware
---

### Post by Lexxus on 2015-03-25
Hi all.

I have a problem.

```

~$ xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; COMPANY USB Device                        id=9    [slave  pointer  (2)]
&#9116;   &#8627; COMPANY USB Device                        id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; COMPANY USB Device                        id=8    [slave  keyboard (3)]
    &#8627; Logitech Gaming Keyboard G105             id=11   [slave  keyboard (3)]
    &#8627; Logitech Gaming Keyboard G105             id=12   [slave  keyboard (3)]
    &#8627; USB Sound Device                          id=13   [slave  keyboard (3)]

```

My mouse detect as COMPANY USB Device (id=9, id=10)
What I need to do to xiunput normally recognized device name??? Simple: COMPANY USB Device -> A4Tech wireless mouse

I do **sudo update-usbids**, but it's not help me.

And my mouse detect in game Metro 2033 (Steam) as joystick. How fix this bug? :?

I use Kubuntu 14.10 x86-64.

Thx :)

---

### Post by Lexxus on 2015-04-03
up, pls help

---

