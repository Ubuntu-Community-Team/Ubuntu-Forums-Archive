---
title: "How can I enable mouse keys from the command line?"
date: 2008-11-25
forum: General Help
---

### Post by transmition on 2008-11-25
Like the title says, how can I enable mouse keys from the command line (The preference from System->Preferences->Keyboard->Mouse Keys->Pointer Can Be Controlled Using The Keypad

The reason being, I would like to make a startup script that would disable and then re enable control of the touchpad using my keyboard on startup, as it manages to either disable itself (untick itself) or stops working and requires itself to be unticked and then reticked. Thanks for any replies.

---

### Post by hkphooey on 2009-05-25
Better late than never. You can use gconftool-2 to get and set values. 

eg. get a value
gconftool-2 --get /desktop/gnome/peripherals/mouse/touchpad_enabled

toggle the value
gconftool-2 --toggle /desktop/gnome/peripherals/mouse/touchpad_enabled

However, on this here Dell, these settings don't seem to be effective. There's something wrong with my touchpad. Grrr. Worked OK in 8.04 and 8.10

---

### Post by hkphooey on 2009-05-25
There are actually two other approaches to this. I wrote them down in my blog,

[http://play.datalude.com/blog/?p=99](http://play.datalude.com/blog/?p=99)

but now neither of those work for me. The ever moving goalposts of Ubuntu.

---

