---
title: "Any way remap/program Logitech &quot;G-keys&quot; in Linux? (xubuntu 14.04)"
date: 2014-09-15
forum: Hardware
---

### Post by AnttiV on 2014-09-15
Running Xubuntu 14.04, but if there's a way in any *nix, then it can probably be used here. So...

Does anyone know how to remap/program the additional "G-Keys" on a Logitech keyboard? With this specific question, the keyboard is the G105 (MW3-version) variety that I got really cheap some years ago. It works otherwise perfectly, but I'd like to remap the six G-keys to other functions (specifically Media buttons, as this keyboard lacks them). They apparently work as F1-F6 keys out of the box (at least System -> Keyboard -> Hotkeys recognize them as such when assigning functions to hotkeys). This is MOSTLY okay, but there are times when I wish they'd be separate keys.

Mac has a wonderful program called "ControllerMate" and while I don't need anything so sophisticated, users of said software know what I'm after. The minimum that I want, is for the system to see the keys separate from the F-keys, I can do most of what I need after that from the hotkey assign preference pane.

I have currently mapped vol up/down to F3/F4 and they work perfectly from G3/G4, but of course if an application has a function on F3...


I found "antimicro", but it doesn't do what I need. While it, in theory, could be what I need, it can only work with USB controllers, NOT a keyboard.

---

### Post by JKyleOKC on 2014-09-15
Take a look at the command-line utility "xev" which will show you the actual scancode for any key; type "man xev" at a command prompt to get directions for using it. Once you know the keycodes, you can use "xmodmap" to assign new actions to each key. To make your assignments permanent, create a bash script with the appropriate commands in it, and add that script to your "autostart" collection.

---

### Post by AnttiV on 2014-09-16
> **JKyleOKC said:**
> Take a look at the command-line utility "xev" which will show you the actual scancode for any key; type "man xev" at a command prompt to get directions for using it. Once you know the keycodes, you can use "xmodmap" to assign new actions to each key. To make your assignments permanent, create a bash script with the appropriate commands in it, and add that script to your "autostart" collection.

Thanks for the reply! It sounded like that'd be the perfect thing and JUST what I'd need, but unfortunately I seem to be out of luck. Not because of the mentioned programs, but because how that keyboard works, it seems.

Here's a copy of xev's output when I press F1 and the G1 keys, sequentially:

```
KeyPress event, serial 37, synthetic NO, window 0x2e00001,
    root 0x2ca, subw 0x0, time 40033438, (81,210), root:(952,685),
    state 0x10, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 37, synthetic NO, window 0x2e00001,
    root 0x2ca, subw 0x0, time 40033542, (81,210), root:(952,685),
    state 0x10, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 37, synthetic NO, window 0x2e00001,
    root 0x2ca, subw 0x0, time 40036956, (81,210), root:(952,685),
    state 0x10, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyRelease event, serial 37, synthetic NO, window 0x2e00001,
    root 0x2ca, subw 0x0, time 40037052, (81,210), root:(952,685),
    state 0x10, keycode 67 (keysym 0xffbe, F1), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
They are identical, so there's (apparently) no way for the system to detect what key I am pressing. I don't know how Logitech does this in a Mac/Win environment, it must have some way to distinguish those keys. Unfortunately, it appears not to be available here.

---

### Post by Bucky Ball on 2014-09-16
If you have the command for what you want to do, then:

Apps>Accessories>Keyboard>App Shortcut keys tab (or something like that)>follow your nose. 'Add' a new shortcut key (F1-6), insert the command and you're done. Perhaps ... :-k

Matter of figuring out an appropriate command, if there is one ...

---

### Post by AnttiV on 2014-09-16
> **Bucky Ball said:**
> If you have the command for what you want to do, then:

Apps>Accessories>Keyboard>App Shortcut keys tab (or something like that)>follow your nose. 'Add' a new shortcut key (F1-6), insert the command and you're done.

Ehh.. quotes from me from the opening post:

> [COLOR=#000000]They apparently work as F1-F6 keys out of the box (at least System -> Keyboard -> Hotkeys recognize them as such when assigning functions to hotkeys). This is MOSTLY okay, but there are times when I wish they'd be separate keys.[/COLOR]

> [COLOR=#000000]I have currently mapped vol up/down to F3/F4 and they work perfectly from G3/G4, but of course if an application has a function on F3...[/COLOR]

I *do* know the command and can use the shortcut tab, but that was not the point. I'd want them (the G-keys) to be *separate* from the F-keys, like they do on Mac/Win.

---

### Post by Bucky Ball on 2014-09-16
Ah, with you. ;)

---

### Post by JKyleOKC on 2014-09-16
> **AnttiV said:**
> Thanks for the reply! It sounded like that'd be the perfect thing and JUST what I'd need, but unfortunately I seem to be out of luck. Not because of the mentioned programs, but because how that keyboard works, it seems.

(xev results snipped)

They are identical, so there's (apparently) no way for the system to detect what key I am pressing. **I don't know how Logitech does this in a Mac/Win environment, it must have some way to distinguish those keys.** Unfortunately, it appears not to be available here.
There must be something done in the lowest-level keyboard driver that's different here; since the Mac/Win actions are different, there's obviously something -- possibly similar to the CTRL-ALT-SHIFT separate status bits -- that tells the proprietary drivers how to distinguish the two keys, and the driver in the X system or in Linux fails to make that distinction.

If you're in a location where the USA's DMCA doesn't apply, you might be able to disassemble the Mac or Win driver code and identify their technique. It's no longer legal to do so in the land of the free, unfortunately. Once the technique is known, however, it would then be perfectly legal to add it to the Linux low-level drivers and solve your problem.

---

### Post by AnttiV on 2014-09-16
> **JKyleOKC said:**
> There must be something done in the lowest-level keyboard driver that's different here; since the Mac/Win actions are different, there's obviously something -- possibly similar to the CTRL-ALT-SHIFT separate status bits -- that tells the proprietary drivers how to distinguish the two keys, and the driver in the X system or in Linux fails to make that distinction.

If you're in a location where the USA's DMCA doesn't apply, you might be able to disassemble the Mac or Win driver code and identify their technique. It's no longer legal to do so in the land of the free, unfortunately. Once the technique is known, however, it would then be perfectly legal to add it to the Linux low-level drivers and solve your problem.

That's probably the only way it can work. Unfortunately - although DMCA does not apply to me (I'm from Finland) - That procedure is way beyond what I can possibly do. I may be able to write a dice rolling program in C++, but disassembling drivers is so far beyond that I might as well learn to fly :)

So this might be it for this venue, at least for now. Thanks for the answers, people, but unless someone comes up with another way, I think I'm stuck trying to get them to work.

---

### Post by 4-launihpad-4 on 2015-05-12
Remapping the Logitech Gnn buttons works well on my Ubuntu 14.04 after installing g15daemon (sudo apt-get install g15daemon), which comes with the standard repository.

I still have a few of the old G15 keyboards that had 18 G-Keys, and using xev, my mapping is

G1-G18  key 175 - 192
M1-M3   key 193 - 195
MR        key 196

You'll still want to remap these keys using xmodmap.

---

