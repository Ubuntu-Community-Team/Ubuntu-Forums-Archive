---
title: "toshiba portege m400"
date: 2012-06-15
forum: Hardware
---

### Post by blurymind on 2012-06-15
Ubuntu precise 64 bit-toshiba m400 tablet pc

I have been trying to assign custom keyboard combinations to this laptop's express keys (the ones on the monitor) and have so far found it Impossible to get the keys to do what I want.

My goal is:
1.map the frigging keycodes of the express keys(the ones on the monitor) of the tablet pc
2.assign custom commands to them (not rotate the screen)


The problem comes from both mapping and assigning the keys.


Executing "xev" command to id the key mapping event, I get two or more events happen (keyboard combination- two keycodes) when I press an express key. So its not giving me the appropriate keycode

assigning the keycode with xmodmap -e is unpredictable- and I dont know to which of the keycodes to assign it. When I do, that ruins the keys that they go for on the keyboard.
So this leads me to believe that the tabletpc expresskeys are executing the keypress event from elsewhere and that triggers the two keycodes as a result


```
**KeymapNotify** event, serial 36, synthetic NO, window 0x0,
   ** keys:  2  ** 4294967168 0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0xb2, subw 0x0, time 13761887, (594,230), root:(595,282),
    state 0x40, **keycode 15** (keysym 0x36, 6), same_screen YES,
    XLookupString gives 1 bytes: (36) "6"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0xb2, subw 0x0, time 13761895, (594,230), root:(595,282),
    state 0x40, keycode 134 (**keysym 0xffec**, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```
Where and what is keysym 0xffec??  What do I do when a key combination is assigned to one button- how do I change it?

---

### Post by Favux on 2012-06-15
Hi blurrymind,

Welcome to Ubuntu forums!

I find key mapping frustrating also.  See the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") esp. appendix 2 on the bottom.  That you should get you up to speed to my hazy level of understanding of the event chain.

---

