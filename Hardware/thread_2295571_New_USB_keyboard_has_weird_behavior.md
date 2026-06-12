---
title: "New USB keyboard has weird behavior"
date: 2015-09-19
forum: Hardware
---

### Post by brian92 on 2015-09-19
So bought a new USB keyboard, but it appears to be doing either nothing, or pressing SHIFT when i press the ALT key.
How would I go about fixing this? My old worn out keyboard still works fine, but I'd rather not return the new one :P

---

### Post by tgalati4 on 2015-09-20
Welcome to the forums.  What is the make and model of the keyboard?

If there is not a proper module (driver) for this keyboard, then you can use *xmodmap* to remap the bad keys.  This is an older keyboard framework, but it can be used to fix certain problems.  The latest versions of Ubuntu use xkb.

Use the old keyboard and print out your current keymap:

```
xmodmap -pk 
xmodmap -pk my_current_keymaps.txt
```

Print out the file.  Plug in your new keyboard and go through each key and mark down its behavior.

Use *xev* to get keycodes and assignments.

Some reading:  [http://askubuntu.com/questions/54157/how-do-i-set-xmodmap-on-login](http://askubuntu.com/questions/54157/how-do-i-set-xmodmap-on-login)

[http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04](http://askubuntu.com/questions/325272/permanent-xmodmap-in-ubuntu-13-04)

[http://askubuntu.com/questions/361128/why-did-13-10-break-my-custom-keyboard-layout/361584#361584](http://askubuntu.com/questions/361128/why-did-13-10-break-my-custom-keyboard-layout/361584#361584)

xkb framework:

[https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions)

[http://askubuntu.com/questions/482678/how-to-add-a-new-keyboard-layout-custom-keyboard-layout-definition](http://askubuntu.com/questions/482678/how-to-add-a-new-keyboard-layout-custom-keyboard-layout-definition)

---

### Post by brian92 on 2015-09-24
Sorry for the late reply, i don't get much spare time to try stuff out :)
It's an ADX Gaming keyboard, small brand only available here in Denmark AFAIK.

According to xev output, both ctrl, alt and alt gr seem to act as shift. Their output is exactly the same:

KeyPress event, serial 37, synthetic NO, window 0x3c00001,
    root 0xd3, subw 0x0, time 1340184, (425,621), root:(491,673),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by tgalati4 on 2015-09-24
My laptop keyboard (the built-in one) shows the following for Control-n, Alt, and Left-Shift keys:

> 
tgalati4@Mint17 ~ $ xev


KeyPress event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97441386, (667,317), root:(673,365),
**    state 0x4, keycode 57 (keysym 0x6e, n), same_screen YES,**
    XLookupString gives 1 bytes: (0e) ""
    XmbLookupString gives 1 bytes: (0e) ""
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97441524, (667,317), root:(673,365),
**    state 0x4, keycode 57 (keysym 0x6e, n), same_screen YES,**
    XLookupString gives 1 bytes: (0e) ""
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97441598, (667,317), root:(673,365),
**    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,**
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97034851, (183,-37), root:(189,11),
**    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,**
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97035023, (183,-37), root:(189,11),
**    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,**
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97035948, (183,-37), root:(189,11),
**    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,**
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4a00001,
    root 0x7f, subw 0x0, time 97036085, (183,-37), root:(189,11),
**    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,**
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


The Control keys don't behave as other keys, you need to use it with another key to get it to register with *xev*.

When you printed out the xmodmap table, what did control, shift, and alt show up as?

> 

     64    	0xffe9 (Alt_L)	0xffe7 (Meta_L)	0xffe9 (Alt_L)	0xffe7 (Meta_L)	

     50    	0xffe1 (Shift_L)	0x0000 (NoSymbol)	0xffe1 (Shift_L)	

     37    	0xffe3 (Control_L)	0x0000 (NoSymbol)	0xffe3 (Control_L)


---

