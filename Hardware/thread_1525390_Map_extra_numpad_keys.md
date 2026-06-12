---
title: "Map extra numpad keys"
date: 2010-07-06
forum: Hardware
---

### Post by theboozler on 2010-07-06
I have a logitech pro 2000 wirless usb keyboard. Everything works fine except for three extra keys just above the numpad, they are an extra equal sign and an open and close parantheses.

How do I get these working?

I'v tried all the different logitch keyboard layouts in the keyboard settings and also a few other models per other's suggestions. No dice.

xev output is the same for all three keys:
KeyPress event, serial 36, synthetic NO, window 0x4200001,
    root 0x142, subw 0x0, time 1468926, (23,69), root:(686,122),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

This is strange because I can configure the keys to work fine in vim via vimrc. Vim outputs the characters ¶±, ´° and ´± when each key is pressed and the terminal outputs 61, 40 and 41. The point is I know the three keys are distinguishable despite xev's output.

I'm running Ubuntu 10.04 32bit

---

### Post by Halibutt on 2011-06-13
Bumping to see if anyone is successful. Have a [similar problem]("http://ubuntuforums.org/showthread.php?p=10934797#post10934797") regarding my Cordless Numpad. 
Cheers

---

