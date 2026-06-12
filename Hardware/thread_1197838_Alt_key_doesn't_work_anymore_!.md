---
title: "Alt key doesn't work anymore !"
date: 2009-06-26
forum: Hardware
---

### Post by antid0te on 2009-06-26
Hello all,

My laptop is Compaq Presario v3738, Ubuntu Jaunty has been installed for about 3 months ago. This afternoon, i migrate my user to another one, copy all stuff from old user to the new one. Now i'm using the new user, but suddenly my ALT keys (Left and Right) does not work (I cannot do Alt+F2 or any shortcut started with Alt key )

I tried to create another account to test if my ALT keys worked but it doesn't. Here's my default Keyboard Model and Layout:

Keyboard Model: Laptop/notebook Compaq (eg. Armada) Laptop Keyboard.
Keyboard layout: USA
Layout Options: (Bold) Key to choose 3rd level --> Any Alt key (checked)

please help, I don't want to reinstall Ubuntu, there's a lot of tweak in my system now :popcorn:

PS: I've searched the internet and this forum, no solution :(

Thx

---

### Post by antid0te on 2009-06-27
Bump! no response..anyone?

---

### Post by benpaka on 2009-09-10
I have the same problem :(

My alt+key doesn't work... I've read many tutorial 
(Change layout options/ changes xorg, ...)

but it still not work...

my output using xev is
```

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

```

For the moment I'm using <Right Win> as the alt+gr and <Left-Win> as Alt, here the output:
```

KeyPress event, serial 33, synthetic NO, window 0x6c00001,
    root 0x1a7, subw 0x6c00002, time 6146892, (49,56), root:(59,147),
    state 0x10, keycode 133 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 33, synthetic NO, window 0x6c00001,
    root 0x1a7, subw 0x0, time 5661457, (170,-16), root:(175,53),
    state 0x10, keycode 133 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 64
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

So this is why i think that the problem is on a lower level.
However, on KDE my keyboard works fine.

---

### Post by qzio on 2009-09-10
I have similar problems.

If i go system->pref->keyboard and click around in the layout options, sometimes it doesn't get saved when i close the dialog, and it doesn't always work

sometime i can get it to work if i use the internal keyboard of my laptop. and the external keyboard can use iso_level3_shift in gnome-terminal/gvim but not in firefox. what's up with that?! :( i cant type the 'at' sign in firefox => i need to type it in a gnome-terminal and then copy/paste so i can log into different sites => not ok. :(

xev gives iso_level3_shift as output both when it's working and when it's not...

does anyone know where the configuration of keyboard layout options is saved?

(p.s all problem started when i upgraded to 9.10)

---

### Post by benpaka on 2009-09-15
It seems that if the Alt_R = level3 is desactivated before shutting down gnome, and it's reactivate after gnome start Alt_R = level3, i can use the alt+gr.

I think I have a conflict somewhere, which block all the key that are assigned to level3 when gnome start (However after the start i can edit the layout manually without any problem)

 - Someone could tell me when the assignation of the layout of gnome is done?
 - Or how to desactivate the layout before shutting down, and reactivate it as the last operation of gnome.

---

