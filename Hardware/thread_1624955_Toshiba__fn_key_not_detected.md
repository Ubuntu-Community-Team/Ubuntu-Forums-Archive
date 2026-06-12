---
title: "Toshiba : fn key not detected"
date: 2010-11-18
forum: Hardware
---

### Post by enimeizoo on 2010-11-18
Hi,
Actually, the fn+key combination work properly (the default ones, fn+F9 to enable/disable the pad, the ones for brightness...) . My problem is that they are not detected by gnome/kde when I try to assign shortcuts. They are not detected by xev, nor xbindkey -k.
It's just like the fn key dosn't exist at all, except for these default shortcuts.
What I wanted was to be able to set it as a modifier, just like control or alt, since I have an empty one. There is no key for Mod3 and I wanted one. 

What I found on the web was people trying to make the default combination work. There was some kind of driver issue, but I'm not sure it's the same problem. 
I also found some threads where it was about fn combinations being acpi events, unlike the usual modifiers combinations. If there isn't a way to consider it as normal keyboard events, I would have to modify the acpi scripts to bind it to Mod3, but I'd prefer avoiding doing stuff I'm not sure about on this kind of file.
Anyway these topics were quite old and I wanted to know if there is anything new about it. 

My laptop is a toshiba satellite, but I believe the problem is the same on all toshiba laptops, unless they changed the fn  key behaviour recently. The os is ubuntu 10.04, I experienced the same issue with both gnome and kde. Actually I don't know what kind of details you would need on the system to answer, so just ask and you'll get them.

Thanks for helping!
(please be forgiving about my english, it's not my mother tongue)

---

### Post by IcarusR on 2010-11-18
> I believe the problem is the same on all toshiba laptops

I have the same on my Tosh Equium A100, it is not limited to Toshibas, my eeepc 901 is the same, the Fn key does not regester in xev.
But on both the basic Fn combinations do work...
Brightness
Volume
Numlock
Print screen
Suspend
Hibernate

I believe the main problem is that the Fn key on it's own does not generate any unique signal/data for Ubuntu to pickup. However when pressed with an F key it does generate unique signal/data.

Do you have a Windows key you could use instead ?

---

### Post by enimeizoo on 2010-11-18
Thanks for answering.
Actually, I already use the windows key, and I don't know what key I could use. I sure could live without it, but I'm curious.

" I believe the main problem is that the Fn key on it's own does not  generate any unique signal/data for Ubuntu to pickup. However when  pressed with an F key it does generate unique signal/data."

I get nothing for a fn+fX combination with xev, but with fn and any other key, I just get the other key. Is there a way to have it sending a keycode? By re-writting a driver or something?

---

### Post by tsg1zzn on 2010-11-18
The Fn key does not send a keycode. It can't be registered by software.

---

### Post by enimeizoo on 2010-11-18
Ok then my fn key will remain a useless key, at the perfect place for a modifier. Poeple who set that up were brillants! I guess I'll just let my control-R do the job.

Thanks anyways!

---

### Post by enimeizoo on 2010-11-19
Actually there is something new. I read that the linux kernel drops keycodes above 255. So is there a way to know whether or not the keyboard sends some of them? 

Besides, some fn+FX combinations send keycodes. So, at least they send a keycode. I think that other ones do, but above the 255 limit, emulated or not.
 
Last question for now, does anyone know what the first event for fnf5 means? It tries to emulate the keycode 8 or something?

It appears for both fnf3 and fnf5, but not always. Only for the second one when I type fnf3 then fnf5, or fnf5 then fnf3. Anyway, thats weird.


Fn+F1 : when F1 pressed/released :
```

KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 26083323, (813,-83), root:(817,598),
    state 0x10, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 26083328, (813,-83), root:(817,598),
    state 0x50, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (6c) "l"
    XmbLookupString gives 1 bytes: (6c) "l"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 26083404, (813,-83), root:(817,598),
    state 0x50, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (6c) "l"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 26083414, (813,-83), root:(817,598),
    state 0x50, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
 
```fn+f3
```
KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 25896461, (-745,271), root:(158,631),
    state 0x10, keycode 150 (keysym 0x1008ff2f, XF86Sleep), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 25896587, (-745,271), root:(158,631),
    state 0x10, keycode 150 (keysym 0x1008ff2f, XF86Sleep), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```fn+f5:
```

MappingNotify event, serial 33, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 25952498, (-284,275), root:(619,635),
    state 0x10, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x9c, subw 0x0, time 25952498, (-284,275), root:(619,635),
    state 0x10, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

