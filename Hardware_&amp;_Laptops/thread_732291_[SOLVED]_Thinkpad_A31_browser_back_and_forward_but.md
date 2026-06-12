---
title: "[SOLVED] Thinkpad A31 browser back and forward buttons not working"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by I Use Dial on 2008-03-22
I miss having the browser back and forward buttons.  The other shortcuts I really didn't use at all.

thinkwiki.org lists a package called 'tpb' which supposedly works better, but when I mark it for install it wants to remove these two packages:

hotkey-setup
ubuntu-desktop

The second one has the following description:

The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.


Is it a good idea for me to remove this package just to get the forward and back buttons?  Is there a better way to fix this?

---

### Post by Whiffle on 2008-03-22
On my t43 those are regular keyboard buttons, what happens when you run "xev" in a terminal, put your cursor in teh white box, and press the buttons?  It should give some keycodes in the terminal window.

---

### Post by I Use Dial on 2008-03-22
The buttons do nothing for me.

First one is back, second one is forward.

KeyRelease event, serial 30, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 3642974134, (166,-13), root:(1341,752),
    state 0x0, keycode 234 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x4400001,
    root 0x59, subw 0x0, time 3642974812, (166,-13), root:(1341,752),
    state 0x0, keycode 233 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by Whiffle on 2008-03-22
But they are showing up as button codes, not something else.  You'll have to set them up using Xmodmap as per this:
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#xmodmap_configuration)

and then make your browser use them, firefox is done like this:
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Firefox](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#Firefox)

---

### Post by I Use Dial on 2008-03-23
Excellent!  Now I know how to modify the xmodmap file.  But which xmodmap file am I using?  I see there are probably over 80 of them in /usr/share/xmodmap folder.

In my keyboard preferences it states that I am using the 'Generic 105-key (intl) PC with U.S. English.  That doesn't seem to translate directly to any of the xmodmap file names I see in the xmodmap folder.

---

### Post by Whiffle on 2008-03-23
You just need to make one called .Xmodmap in your home directory, it should be loaded by gnome on startup ( i think it pops up a window asking what to do with it)

---

### Post by I Use Dial on 2008-03-23
It works!  Thank you!!

---

