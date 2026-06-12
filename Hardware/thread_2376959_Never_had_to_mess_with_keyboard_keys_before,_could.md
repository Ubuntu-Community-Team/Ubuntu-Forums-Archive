---
title: "Never had to mess with keyboard keys before, could use a hand"
date: 2017-11-07
forum: Hardware
---

### Post by accounts0 on 2017-11-07
I recently got a Logitech solar keyboard [1], & I like it well enough, but it's missing a key I used to take for granted. The one on the lower right between Ctrl & Alt that was the equivalent to right-clicking the mouse.

I have a blue 'FN' key there now- no idea what it is. Wondering if there's a way to make that key I'm longing for happen from this new, alien blue one.

Possible?


[1]
[https://secure.logitech.com/en-us/product/k750-keyboard](https://secure.logitech.com/en-us/product/k750-keyboard)

---

### Post by efflandt on 2017-11-09
The blue FN key modifies the function of any keys to whatever those keys have in blue on them, similar to a shift key. Some keyboards (like many laptops and Logitech K400) actually have function of numbered F# keys reversed where ACPI functions are primary and numbered function keys are secondary using the FN key. But my small wireless K400 keyboard includes a mousepad which has left and right mouse buttons.

I was going to ask what symbol was on that key, but when I look at my Microsoft Sidewinder X4 keyboard, it has such a key with symbol on it appearing to be a cursor arrow highlighting something on a list and does the same as right clicking a mouse. If I run **xev** it actually shows that as a "Menu" key. Not sure how to program another key to do that, but this is what xev shows for pressing and releasing that key:```
KeyPress event, serial 37, synthetic NO, window 0x4800001,
    root 0x1da, subw 0x0, time 1282939377, (-164,335), root:(570,387),
    state 0x0, keycode 135 (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4800001,
    root 0x1da, subw 0x0, time 1282939501, (-164,335), root:(570,387),
    state 0x0, keycode 135 (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```So maybe someone else could help tell you how to assign that to another key or key combination.

---

### Post by accounts0 on 2017-11-09
Hmm, a function modifier key sounds like it might be difficult to re-map. I had tried some time ago to map the "Windows" key to bring up the KDE "Start Button" Menu, but was unable because that key didn't do anything by itself except change whatever was pressed with it to something other than whatever that key would be when pressed without that key- again, like a "Shift".

Personally, I only need to use the keys that share buttons with the "F#" keys when using the laptop's built-in keyboard.

Hopefully, someone else may have a better understanding & be able to provide a solution here.

---

### Post by accounts0 on 2017-12-01
bump

---

### Post by accounts0 on 2017-12-13
Seems this keyboard won't be able to provide the desired function on that key. Bummer.

---

