---
title: "Mouse sensitivity problem"
date: 2010-04-30
forum: Hardware
---

### Post by MeanEYE on 2010-04-30
Again, age old issue with mice with resolution > 300dpi. :/

In last version of Ubuntu (9.10) this issue was simply resolved by creating HAL policy file and everything went on just fine... But in 10.04 this is not the case. I can't find HAL at all on this version and policy files do nothing.

Ubuntu team should have done something about this. Every release faces the same problem. :/ We need a normal mouse utility! :D

Anyone has any idea how to fix this unusable mouse issue?

---

### Post by MeanEYE on 2010-04-30
*bump*

---

### Post by aleko74 on 2010-05-09
I have the same issue after upgrading from 9.10 to 10.04. Has anybody resolved this?

---

### Post by MeanEYE on 2010-05-09
> **aleko74 said:**
> I have the same issue after upgrading from 9.10 to 10.04. Has anybody resolved this?

As far as I see ... no one:/

Luckily for me... I have Logitech G9 mouse on my desktop with preconfigured profile for Linux (reduced resolution and sensitivity) but my laptop mouse is unusable...

---

### Post by MeanEYE on 2010-05-16
For all those who have similar problems with their pointers. 

You can find solution [here]("http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10"). Basically it's simply setting xinput parameters.

---

### Post by stark dar on 2010-09-23
Okay, I've done all this, the response I get is:

starkdar@starkdar:~$ xinput --list --short
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer DeathAdder                      id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
starkdar@starkdar:~$ 

I type:

xinput [COLOR=#660033]--set-prop[/COLOR] [COLOR=#ff0000]"Razer Razer DeathAdder"[/COLOR] [COLOR=#ff0000]"Device Accel Constant Deceleration"[/COLOR] [COLOR=#000000]5      

[/COLOR]It tells me:

unable to find device Razer Razer DeathAdder

I have tried many combinations, I am very new to Linux, recently switched from XP.

Thanks in advance for any help!

---

### Post by MeanEYE on 2010-09-23
> **stark dar said:**
> Okay, I've done all this, the response I get is:

starkdar@starkdar:~$ xinput --list --short
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer DeathAdder                      id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
starkdar@starkdar:~$ 

I type:

xinput [COLOR=#660033]--set-prop[/COLOR] [COLOR=#ff0000]"Razer Razer DeathAdder"[/COLOR] [COLOR=#ff0000]"Device Accel Constant Deceleration"[/COLOR] [COLOR=#000000]5      

[/COLOR]It tells me:

unable to find device Razer Razer DeathAdder

I have tried many combinations, I am very new to Linux, recently switched from XP.

Thanks in advance for any help!

Try just with "Razer DeathAdder" ;).

---

### Post by aleko74 on 2010-09-23
stark dar,

Try using the id instead of name:

xinput --set-prop 10 "Device Accel Constant Deceleration" 5

---

### Post by stark dar on 2010-09-23
Boo Ya! Thanks Aleko, file it under SOLVED!

---

