---
title: "Is my wacom bamboo pen faulty ?"
date: 2011-07-09
forum: Hardware
---

### Post by FrostBlue on 2011-07-09
Hi,
I have a wacom bamboo MTE-450 which was giving me some trouble before. But is the matter got resolved after changing the threshold value. 
Now the left click doesn't work at all. Even the eraser doesn't click.

MMB and RMB work just fine.

Can anyone help ?

I am on Maverick with backports and no launchpad.

Here are outputs of some commands which I used before

xinput list :

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo stylus                       id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo eraser                       id=13   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo cursor                       id=14   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo pad                          id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]


xsetwacom list :

Wacom Bamboo stylus                     id: 10  type: STYLUS    
Wacom Bamboo eraser                     id: 13  type: ERASER    
Wacom Bamboo cursor                     id: 14  type: CURSOR    
Wacom Bamboo pad                        id: 15  type: PAD

---

### Post by FrostBlue on 2011-07-09
When I try to click something, the pointer highlights the button, but Left click doesn't register at all. I have tried changing threshold to 10 and other values.
Is there a way to change MMB to Left click.

I am going to try this on Windows and see if it works over there.

---

### Post by wandalalakers on 2011-07-09
This might be reaching but if you know anyone with a windows machine, try it using that and download the Wacom driver for windows. At least you will know if the pen works.

---

### Post by FrostBlue on 2011-07-09
I checked on Windows, click doesn't always work there.Sometimes does. But both MMB and RMB click work great.
I am looking into buying a new one.

---

