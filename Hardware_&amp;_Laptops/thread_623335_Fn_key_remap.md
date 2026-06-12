---
title: "Fn key remap"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by dracker on 2007-11-25
I finally discovered why I can't change my screen brightness, the Fn + UP and Fn + Down is not mapped. With xev I got:


For Fn + Up
KeyPress event, serial 31, synthetic NO, window 0x4000001,
    root 0x52, subw 0x0, time 2033377731, (163,-16), root: (170,499),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4000001,
    root 0x52, subw 0x0, time 2033377731, (163,-16), root: (170,499),
    state 0x0, keycode 212 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


For Fn + Down:
KeyPress event, serial 31, synthetic NO, window 0x4000001,
    root 0x52, subw 0x0, time 2033379123, (163,-16), root: (170,499),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4000001,
    root 0x52, subw 0x0, time 2033379124, (163,-16), root: (170,499),
    state 0x0, keycode 101 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

The other key asociated to screen brightness is Fn+F8, this one works perfectly but only adjust it to maximum or minimum, also this combination shows nothing on xev so I guess all this is not an X problem, also any app that controls screen brightness works.
So, I know this has nothing to do with the keyboard layout but with something else.
I google a little bit and found that xmodmap can be used to map the keys, but I don-t have any idea of the command to associate Fn+Up/Down to adjust screen brightness, 
So, any of the Ubuntu professionals knows how to map the Fn+Up/Down key? I know this is somewhere hidden inside the kernel... 
By the way, mine is a Gateway MX6448 with AMD Turion 64x2.
Please help :(

---

### Post by khnz on 2007-11-25
You only need the keycode (from xev) for xmodmap. Try this to map the key:
 xmodmap -e "keymap 212 = SunVideoLowerBrightness"
 xmodmap -e "keymap 101 = SunVideoRaiseBrightness"

---

### Post by dracker on 2007-11-26
Thank you for your answer khnz but when I type those:

> **khnz said:**
> 
 xmodmap -e "keymap 212 = SunVideoLowerBrightness"
 xmodmap -e "keymap 101 = SunVideoRaiseBrightness"

I get in both cases:

xmodmap:  unknown command on line commandline:1
xmodmap:  1 error encountered, aborting.

But can you please tell me where did you find those? maybe I can find the right one for my gateway laptop.

---

### Post by khnz on 2007-11-26
Argh, sorry, replace keymap with keycode.

The keycode comes from your xev output, the keysym from /usr/share/X11/XKeysymDB (don't know if this the right Symbols, but it works fine on my box).

---

### Post by dracker on 2007-11-26
I mapped the keys fine now... but screen brightness is still unchanged :(

---

### Post by khnz on 2007-11-26
Are you using gnome?
Does the brightness control work at all? (meant does gnome brightness applet work, for example)

---

### Post by dracker on 2007-11-26
Yes, I'm on Gnome but the screen brightness applet does nothing, it shows a red x in it (the panel one).
My keyboard has 3 keys to control screen brightness, one just adjust it to its maximum or minimum, that one works fine but when pressed shows nothing on kev, and the other 2 are the ones that adjust the brightness step by step (Fn + UP and Fn + Down) that ones shows on kev but does nothing even after mapping them... Somebody told me that some keys like the ones that control the brightness are not controled by Ubuntu but by the BIOS, but Ubuntu has to be setted up to pass the info directly to BIOS... maybe that's the problem, I really don't know.
As extra info everything works ok (all 3 keys) in BIOS and GRUB, but once I get to usplash the Fn+UP/Down stop working. Also they work perfectly when using the Gparted live cd (I think this one uses gnome as well).
Hope this gives you a clue of what's going on, thanks a lot for your help!

---

### Post by khnz on 2007-11-27
Sorry, no idea (don't know this hardware). But you can try to find your video card in hal-device-manager and check if it has the laptop_panel capability. If not, brightness control is not supported or hal doesn't know how to do.

---

### Post by dracker on 2007-11-30
Unfortunately Gateway is not that popular... HP, Sun and IBM has special commands to manage this... Still looking for a solution :(

---

